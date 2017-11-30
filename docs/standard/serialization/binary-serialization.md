---
title: "Sérialisation binaire"
ms.date: 08/11/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
caps.latest.revision: "5"
author: ViktorHofer
ms.author: mairaw
ms.openlocfilehash: 74ee4e21934c1e4f3fd008664b1315429dc47b37
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="binary-serialization"></a><span data-ttu-id="c5752-102">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="c5752-102">Binary serialization</span></span>

<span data-ttu-id="c5752-103">La sérialisation peut être définie comme le processus de stockage de l'état d'un objet sur un support de stockage.</span><span class="sxs-lookup"><span data-stu-id="c5752-103">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="c5752-104">Pendant ce processus, les champs publics et privés de l'objet et le nom de la classe, y compris l'assembly contenant la classe, sont convertis en un flux de données d'octets, écrit ensuite dans un flux de données.</span><span class="sxs-lookup"><span data-stu-id="c5752-104">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="c5752-105">Lorsque l'objet est désérialisé par la suite, un clone exact de l'objet d'origine est créé.</span><span class="sxs-lookup"><span data-stu-id="c5752-105">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="c5752-106">Lorsque vous implémentez un mécanisme de sérialisation dans un environnement orienté objet, vous devez faire plusieurs compromis entre facilité d'utilisation et souplesse.</span><span class="sxs-lookup"><span data-stu-id="c5752-106">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="c5752-107">Le processus peut être automatisé en grande partie, à condition que vous puissiez suffisamment le contrôler.</span><span class="sxs-lookup"><span data-stu-id="c5752-107">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="c5752-108">Par exemple, dans certaines situations, la sérialisation binaire simple n'est pas suffisante ou une raison particulière peut exiger la définition des champs à sérialiser.</span><span class="sxs-lookup"><span data-stu-id="c5752-108">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="c5752-109">Les sections suivantes étudient le mécanisme de sérialisation fiable fourni avec .NET et mettent en évidence plusieurs fonctionnalités importantes qui vous permettent de personnaliser le processus en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="c5752-109">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="c5752-110">L'état d'un objet encodé UTF-8 ou UTF-7 n'est pas préservé si l'objet est sérialisé et désérialisé à l'aide de différentes versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5752-110">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="c5752-111">Étant donné que la nature de la sérialisation binaire autorise la modification des membres privés à l’intérieur d’un objet, et par conséquent la modification de l’état de ce dernier, d’autres infrastructures de sérialisation qui opèrent sur la surface publique de l’API, comme JSON.NET, sont recommandées.</span><span class="sxs-lookup"><span data-stu-id="c5752-111">As the nature of binary serialization allows the modification of private members inside an object and therefore changing the state of it, other serialization frameworks like JSON.NET which operate on the public API surface are recommended.</span></span>

## <a name="binary-serialization-in-net-core"></a><span data-ttu-id="c5752-112">Sérialisation binaire dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="c5752-112">Binary serialization in .NET Core</span></span>

<span data-ttu-id="c5752-113">.NET Core prend en charge la sérialisation binaire avec un sous-ensemble de types.</span><span class="sxs-lookup"><span data-stu-id="c5752-113">.NET Core supports binary serialization with a subset of types.</span></span> <span data-ttu-id="c5752-114">Vous trouverez la liste des types pris en charge dans la section [Types sérialisables](#serializable-types).</span><span class="sxs-lookup"><span data-stu-id="c5752-114">You can see the list of supported types in the [Serializable types section](#serializable-types).</span></span> <span data-ttu-id="c5752-115">L’ensemble défini des types est garanti comme étant sérialisable entre le .NET Framework 4.5.1 et versions ultérieures et .NET Core 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c5752-115">The defined set of types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="c5752-116">D’autres implémentations de .NET, tels que Mono, ne sont pas officiellement prises en charge mais devraient également fonctionner.</span><span class="sxs-lookup"><span data-stu-id="c5752-116">Other .NET implementations, such as Mono, aren't officially supported but should also be working.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="c5752-117">Types sérialisables</span><span class="sxs-lookup"><span data-stu-id="c5752-117">Serializable types</span></span>

- <xref:System.AggregateException?displayProperty=nameWithType>   
- <xref:System.Array?displayProperty=nameWithType>   
- <xref:System.ArraySegment%601?displayProperty=nameWithType>   
- <xref:System.Attribute?displayProperty=nameWithType>   
- <xref:System.Boolean?displayProperty=nameWithType>   
- <xref:System.Byte?displayProperty=nameWithType>   
- <xref:System.Char?displayProperty=nameWithType>   
- <xref:System.Collections.ArrayList?displayProperty=nameWithType>   
- <xref:System.Collections.BitArray?displayProperty=nameWithType>   
- <xref:System.Collections.Comparer?displayProperty=nameWithType>   
- <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>   
- <xref:System.Collections.Hashtable?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.Queue?displayProperty=nameWithType>   
- <xref:System.Collections.SortedList?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Stack?displayProperty=nameWithType>   
- <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType>   
- <span data-ttu-id="c5752-118"><xref:System.DBNull?displayProperty=nameWithType>(disponible dans .NET Core 2.0.2 et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="c5752-118"><xref:System.DBNull?displayProperty=nameWithType> (available in .NET Core 2.0.2 and later versions)</span></span>   
- <xref:System.Data.DataSet?displayProperty=nameWithType>   
- <xref:System.Data.DataTable?displayProperty=nameWithType>   
- <xref:System.Data.PropertyCollection?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType>   
- <xref:System.DateTime?displayProperty=nameWithType>   
- <xref:System.DateTimeOffset?displayProperty=nameWithType>   
- <xref:System.Decimal?displayProperty=nameWithType>   
- <xref:System.Double?displayProperty=nameWithType>   
- <xref:System.Drawing.Color?displayProperty=nameWithType>   
- <xref:System.Drawing.Point?displayProperty=nameWithType>   
- <xref:System.Drawing.PointF?displayProperty=nameWithType>   
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>   
- <xref:System.Drawing.RectangleF?displayProperty=nameWithType>   
- <xref:System.Drawing.Size?displayProperty=nameWithType>   
- <xref:System.Drawing.SizeF?displayProperty=nameWithType>   
- <xref:System.Enum?displayProperty=nameWithType>   
- <xref:System.Exception?displayProperty=nameWithType>   
- <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>   
- <xref:System.Globalization.SortVersion?displayProperty=nameWithType>   
- <xref:System.Guid?displayProperty=nameWithType>   
- <xref:System.Int16?displayProperty=nameWithType>   
- <xref:System.Int32?displayProperty=nameWithType>   
- <xref:System.Int64?displayProperty=nameWithType>   
- <xref:System.IntPtr?displayProperty=nameWithType>   
- <xref:System.Net.Cookie?displayProperty=nameWithType>   
- <xref:System.Net.CookieCollection?displayProperty=nameWithType>   
- <xref:System.Net.CookieContainer?displayProperty=nameWithType>   
- <xref:System.Nullable%601?displayProperty=nameWithType>   
- <xref:System.Numerics.BigInteger?displayProperty=nameWithType>   
- <xref:System.Numerics.Complex?displayProperty=nameWithType>   
- <xref:System.Object?displayProperty=nameWithType>   
- <xref:System.SByte?displayProperty=nameWithType>   
- <xref:System.Single?displayProperty=nameWithType>   
- <xref:System.String?displayProperty=nameWithType>   
- <xref:System.StringComparer?displayProperty=nameWithType>   
- <xref:System.Text.StringBuilder?displayProperty=nameWithType>   
- <xref:System.TimeSpan?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType>   
- <xref:System.Tuple?displayProperty=nameWithType>   
- <xref:System.UInt16?displayProperty=nameWithType>   
- <xref:System.UInt32?displayProperty=nameWithType>   
- <xref:System.UInt64?displayProperty=nameWithType>   
- <xref:System.UIntPtr?displayProperty=nameWithType>   
- <xref:System.Uri?displayProperty=nameWithType>   
- <span data-ttu-id="c5752-119"><xref:System.ValueTuple?displayProperty=nameWithType>(non sérialisable dans .NET Framework 4.7 et versions antérieures)</span><span class="sxs-lookup"><span data-stu-id="c5752-119"><xref:System.ValueTuple?displayProperty=nameWithType> (not serializable in .NET Framework 4.7 and earlier versions)</span></span>  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   

## <a name="in-this-section"></a><span data-ttu-id="c5752-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c5752-120">In this section</span></span>

 [<span data-ttu-id="c5752-121">Concepts de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="c5752-121">Serialization Concepts</span></span>](../../../docs/standard/serialization/serialization-concepts.md)  
 <span data-ttu-id="c5752-122">Aborde deux scénarios où la sérialisation est utile : conservation des données en stockage et passage d'objets sur des domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="c5752-122">Discusses two scenarios where serialization is useful: when persisting data to storage and when passing objects across application domains.</span></span>  
  
 [<span data-ttu-id="c5752-123">Sérialisation de base</span><span class="sxs-lookup"><span data-stu-id="c5752-123">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 <span data-ttu-id="c5752-124">Décrit comment utiliser les formateurs binaires et SOAP pour sérialiser des objets.</span><span class="sxs-lookup"><span data-stu-id="c5752-124">Describes how to use the binary and SOAP formatters to serialize objects.</span></span>  
  
 [<span data-ttu-id="c5752-125">Sérialisation sélective</span><span class="sxs-lookup"><span data-stu-id="c5752-125">Selective Serialization</span></span>](../../../docs/standard/serialization/selective-serialization.md)  
 <span data-ttu-id="c5752-126">Décrit comment empêcher certains membres d'une classe d'être sérialisés.</span><span class="sxs-lookup"><span data-stu-id="c5752-126">Describes how to prevent some members of a class from being serialized.</span></span>  
  
 [<span data-ttu-id="c5752-127">Sérialisation personnalisée</span><span class="sxs-lookup"><span data-stu-id="c5752-127">Custom Serialization</span></span>](../../../docs/standard/serialization/custom-serialization.md)  
 <span data-ttu-id="c5752-128">Décrit comment personnaliser la sérialisation d’une classe en utilisant l’interface <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="c5752-128">Describes how to customize serialization for a class by using the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 [<span data-ttu-id="c5752-129">Étapes du processus de sérialisation</span><span class="sxs-lookup"><span data-stu-id="c5752-129">Steps in the Serialization Process</span></span>](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 <span data-ttu-id="c5752-130">Décrit le plan d'action de la sérialisation lorsque la méthode <xref:System.Runtime.Serialization.Formatter.Serialize%2A> est appelée sur un formateur.</span><span class="sxs-lookup"><span data-stu-id="c5752-130">Describes the course of action serialization takes when the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a formatter.</span></span>  
  
 [<span data-ttu-id="c5752-131">Sérialisation avec tolérance de version</span><span class="sxs-lookup"><span data-stu-id="c5752-131">Version Tolerant Serialization</span></span>](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 <span data-ttu-id="c5752-132">Explique comment créer des types sérialisables qui peuvent être modifiés avec le temps sans que les applications ne lèvent d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="c5752-132">Explains how to create serializable types that can be modified over time without causing applications to throw exceptions.</span></span>  
  
 [<span data-ttu-id="c5752-133">Indications concernant la sérialisation</span><span class="sxs-lookup"><span data-stu-id="c5752-133">Serialization Guidelines</span></span>](../../../docs/standard/serialization/serialization-guidelines.md)  
 <span data-ttu-id="c5752-134">Fournit des indications générales pour décider quand sérialiser un objet.</span><span class="sxs-lookup"><span data-stu-id="c5752-134">Provides some general guidelines for deciding when to serialize an object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c5752-135">Référence</span><span class="sxs-lookup"><span data-stu-id="c5752-135">Reference</span></span>  
 <xref:System.Runtime.Serialization>  
 <span data-ttu-id="c5752-136">Contient des classes qui peuvent être utilisées pour sérialiser et désérialiser des objets.</span><span class="sxs-lookup"><span data-stu-id="c5752-136">Contains classes that can be used for serializing and deserializing objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c5752-137">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="c5752-137">Related sections</span></span>  
 [<span data-ttu-id="c5752-138">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="c5752-138">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 <span data-ttu-id="c5752-139">Décrit le mécanisme de sérialisation XML inclus avec le Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="c5752-139">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>  
  
 [<span data-ttu-id="c5752-140">Sécurité et sérialisation</span><span class="sxs-lookup"><span data-stu-id="c5752-140">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)  
 <span data-ttu-id="c5752-141">Décrit les indications de codage sécurisé à suivre lors de l'écriture du code qui exécute la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="c5752-141">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>  
  
 [<span data-ttu-id="c5752-142">Objets distants</span><span class="sxs-lookup"><span data-stu-id="c5752-142">Remote Objects</span></span>](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 <span data-ttu-id="c5752-143">Décrit les différentes méthodes de communication disponibles dans le .NET Framework pour les communications distantes.</span><span class="sxs-lookup"><span data-stu-id="c5752-143">Describes the various communications methods available in the .NET Framework for remote communications.</span></span>  
  
 [<span data-ttu-id="c5752-144">Création de services Web XML à l’aide de clients de service Web XML et ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c5752-144">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 <span data-ttu-id="c5752-145">Fournit des rubriques qui décrivent et expliquent comment programmer des services Web XML créés à l'aide d'ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c5752-145">Provides topics that describe and explain how to program XML Web services created using ASP.NET.</span></span>
