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
- <xref:System.DBNull?displayProperty=nameWithType>(disponible dans .NET Core 2.0.2 et versions ultérieures)   
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
- <xref:System.ValueTuple?displayProperty=nameWithType>(non sérialisable dans .NET Framework 4.7 et versions antérieures)  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   

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
