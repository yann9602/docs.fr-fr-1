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
caps.latest.revision: 5
author: ViktorHofer
ms.author: mairaw
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 995430b2426cb124ee889ed49cc7260c68138151
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="binary-serialization"></a>Sérialisation binaire

La sérialisation peut être définie comme le processus de stockage de l'état d'un objet sur un support de stockage. Pendant ce processus, les champs publics et privés de l'objet et le nom de la classe, y compris l'assembly contenant la classe, sont convertis en un flux de données d'octets, écrit ensuite dans un flux de données. Lorsque l'objet est désérialisé par la suite, un clone exact de l'objet d'origine est créé.

Lorsque vous implémentez un mécanisme de sérialisation dans un environnement orienté objet, vous devez faire plusieurs compromis entre facilité d'utilisation et souplesse. Le processus peut être automatisé en grande partie, à condition que vous puissiez suffisamment le contrôler. Par exemple, dans certaines situations, la sérialisation binaire simple n'est pas suffisante ou une raison particulière peut exiger la définition des champs à sérialiser. Les sections suivantes étudient le mécanisme de sérialisation fiable fourni avec .NET et mettent en évidence plusieurs fonctionnalités importantes qui vous permettent de personnaliser le processus en fonction de vos besoins.

> [!NOTE]
> L'état d'un objet encodé UTF-8 ou UTF-7 n'est pas préservé si l'objet est sérialisé et désérialisé à l'aide de différentes versions du .NET Framework.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Étant donné que la nature de la sérialisation binaire autorise la modification des membres privés à l’intérieur d’un objet, et par conséquent la modification de l’état de ce dernier, d’autres infrastructures de sérialisation qui opèrent sur la surface publique de l’API, comme JSON.NET, sont recommandées.

## <a name="binary-serialization-in-net-core"></a>Sérialisation binaire dans .NET Core

.NET Core prend en charge la sérialisation binaire avec un sous-ensemble de types. Vous trouverez la liste des types pris en charge dans la section [Types sérialisables](#serializable-types). L’ensemble défini des types est garanti comme étant sérialisable entre le .NET Framework 4.5.1 et versions ultérieures et .NET Core 2.0 et versions ultérieures. D’autres implémentations de .NET, tels que Mono, ne sont pas officiellement prises en charge mais devraient également fonctionner.

### <a name="serializable-types"></a>Types sérialisables

- <xref:System.AggregateException?displayProperty=fullName>   
- <xref:System.Array?displayProperty=fullName>   
- <xref:System.ArraySegment%601?displayProperty=fullName>   
- <xref:System.Attribute?displayProperty=fullName>   
- <xref:System.Boolean?displayProperty=fullName>   
- <xref:System.Byte?displayProperty=fullName>   
- <xref:System.Char?displayProperty=fullName>   
- <xref:System.Collections.ArrayList?displayProperty=fullName>   
- <xref:System.Collections.BitArray?displayProperty=fullName>   
- <xref:System.Collections.Comparer?displayProperty=fullName>   
- <xref:System.Collections.DictionaryEntry?displayProperty=fullName>   
- <xref:System.Collections.Generic.Comparer%601?displayProperty=fullName>   
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>   
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=fullName>   
- <xref:System.Collections.Generic.HashSet%601?displayProperty=fullName>   
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=fullName>   
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=fullName>   
- <xref:System.Collections.Generic.List%601?displayProperty=fullName>   
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>   
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>   
- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>   
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName>   
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>   
- <xref:System.Collections.Hashtable?displayProperty=fullName>   
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>   
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>   
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=fullName>   
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>   
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=fullName>   
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=fullName>   
- <xref:System.Collections.Queue?displayProperty=fullName>   
- <xref:System.Collections.SortedList?displayProperty=fullName>   
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>   
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>   
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>   
- <xref:System.Collections.Specialized.StringCollection?displayProperty=fullName>   
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=fullName>   
- <xref:System.Collections.Stack?displayProperty=fullName>   
- <xref:System.ComponentModel.BindingList%601?displayProperty=fullName>   
- <xref:System.Data.DataSet?displayProperty=fullName>   
- <xref:System.Data.DataTable?displayProperty=fullName>   
- <xref:System.Data.PropertyCollection?displayProperty=fullName>   
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=fullName>   
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=fullName>   
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=fullName>   
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=fullName>   
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=fullName>   
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=fullName>   
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=fullName>   
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=fullName>   
- <xref:System.Data.SqlTypes.SqlString?displayProperty=fullName>   
- <xref:System.DateTime?displayProperty=fullName>   
- <xref:System.DateTimeOffset?displayProperty=fullName>   
- <xref:System.Decimal?displayProperty=fullName>   
- <xref:System.Double?displayProperty=fullName>   
- <xref:System.Drawing.Color?displayProperty=fullName>   
- <xref:System.Drawing.Point?displayProperty=fullName>   
- <xref:System.Drawing.PointF?displayProperty=fullName>   
- <xref:System.Drawing.Rectangle?displayProperty=fullName>   
- <xref:System.Drawing.RectangleF?displayProperty=fullName>   
- <xref:System.Drawing.Size?displayProperty=fullName>   
- <xref:System.Drawing.SizeF?displayProperty=fullName>   
- <xref:System.Enum?displayProperty=fullName>   
- <xref:System.Exception?displayProperty=fullName>   
- <xref:System.Globalization.CompareInfo?displayProperty=fullName>   
- <xref:System.Globalization.SortVersion?displayProperty=fullName>   
- <xref:System.Guid?displayProperty=fullName>   
- <xref:System.Int16?displayProperty=fullName>   
- <xref:System.Int32?displayProperty=fullName>   
- <xref:System.Int64?displayProperty=fullName>   
- <xref:System.IntPtr?displayProperty=fullName>   
- <xref:System.Net.Cookie?displayProperty=fullName>   
- <xref:System.Net.CookieCollection?displayProperty=fullName>   
- <xref:System.Net.CookieContainer?displayProperty=fullName>   
- <xref:System.Nullable%601?displayProperty=fullName>   
- <xref:System.Numerics.BigInteger?displayProperty=fullName>   
- <xref:System.Numerics.Complex?displayProperty=fullName>   
- <xref:System.Object?displayProperty=fullName>   
- <xref:System.SByte?displayProperty=fullName>   
- <xref:System.Single?displayProperty=fullName>   
- <xref:System.String?displayProperty=fullName>   
- <xref:System.StringComparer?displayProperty=fullName>   
- <xref:System.Text.StringBuilder?displayProperty=fullName>   
- <xref:System.TimeSpan?displayProperty=fullName>   
- <xref:System.TimeZoneInfo?displayProperty=fullName>   
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=fullName>   
- <xref:System.Tuple?displayProperty=fullName>   
- <xref:System.UInt16?displayProperty=fullName>   
- <xref:System.UInt32?displayProperty=fullName>   
- <xref:System.UInt64?displayProperty=fullName>   
- <xref:System.UIntPtr?displayProperty=fullName>   
- <xref:System.Uri?displayProperty=fullName>   
- <xref:System.ValueTuple?displayProperty=fullName>   
- <xref:System.ValueType?displayProperty=fullName>   
- <xref:System.Version?displayProperty=fullName>   
- <xref:System.WeakReference?displayProperty=fullName>   
- <xref:System.WeakReference%601?displayProperty=fullName>   

## <a name="in-this-section"></a>Dans cette section

 [Concepts de la sérialisation](../../../docs/standard/serialization/serialization-concepts.md)  
 Aborde deux scénarios où la sérialisation est utile : conservation des données en stockage et passage d'objets sur des domaines d'application.  
  
 [Sérialisation de base](../../../docs/standard/serialization/basic-serialization.md)  
 Décrit comment utiliser les formateurs binaires et SOAP pour sérialiser des objets.  
  
 [Sérialisation sélective](../../../docs/standard/serialization/selective-serialization.md)  
 Décrit comment empêcher certains membres d'une classe d'être sérialisés.  
  
 [Sérialisation personnalisée](../../../docs/standard/serialization/custom-serialization.md)  
 Décrit comment personnaliser la sérialisation d’une classe en utilisant l’interface <xref:System.Runtime.Serialization.ISerializable>.  
  
 [Étapes du processus de sérialisation](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 Décrit le plan d'action de la sérialisation lorsque la méthode <xref:System.Runtime.Serialization.Formatter.Serialize%2A> est appelée sur un formateur.  
  
 [Sérialisation avec tolérance de version](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 Explique comment créer des types sérialisables qui peuvent être modifiés avec le temps sans que les applications ne lèvent d'exceptions.  
  
 [Indications concernant la sérialisation](../../../docs/standard/serialization/serialization-guidelines.md)  
 Fournit des indications générales pour décider quand sérialiser un objet.  
  
## <a name="reference"></a>Référence  
 <xref:System.Runtime.Serialization>  
 Contient des classes qui peuvent être utilisées pour sérialiser et désérialiser des objets.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Sérialisation XML et SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Décrit le mécanisme de sérialisation XML inclus avec le Common Language Runtime.  
  
 [Sécurité et sérialisation](../../../docs/framework/misc/security-and-serialization.md)  
 Décrit les indications de codage sécurisé à suivre lors de l'écriture du code qui exécute la sérialisation.  
  
 [Objets distants](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 Décrit les différentes méthodes de communication disponibles dans le .NET Framework pour les communications distantes.  
  
 [Création de services Web XML à l’aide de clients de service Web XML et ASP.NET](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 Fournit des rubriques qui décrivent et expliquent comment programmer des services Web XML créés à l'aide d'ASP.NET.

