---
title: Noms de classes, de structures et d'interfaces
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a4f4b9e48587138f3e65c0c6825af0b3e4e8c592
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-classes-structs-and-interfaces"></a>Noms de classes, de structures et d'interfaces
Les instructions d’affectation de noms qui suivent s’appliquent aux noms de type général.  
  
 **✓ FAIRE** un nom de classes et structs avec des noms ou des expressions nominales, à l’aide de la casse Pascal.  
  
 Cela permet de différencier les noms de types, ces méthodes sont nommées avec verbaux.  
  
 **✓ FAIRE** nom interfaces phrases adjectivales ou parfois avec des noms ou des expressions nominales.  
  
 Les noms et des expressions nominales doivent être utilisées rarement et ils peuvent indiquer que le type doit être une classe abstraite et pas une interface.  
  
 **X ne sont pas** donner des noms de classe un préfixe (par exemple, « C »).  
  
 **✓ Envisagez** se terminant par le nom de classes dérivées portant le nom de la classe de base.  
  
 Cela est très lisible et explique la relation clairement. Voici quelques exemples de ce code : `ArgumentOutOfRangeException`, qui est une sorte de `Exception`, et `SerializableAttribute`, qui est un type de `Attribute`. Toutefois, il est important d’utiliser les Réfléchissez soigneusement en appliquant cette indication ; par exemple, le `Button` classe est une sorte de `Control` événement, bien que `Control` n’apparaît pas dans son nom.  
  
 **✓ FAIRE** préfixe les noms d’interface avec la lettre I, pour indiquer que le type est une interface.  
  
 Par exemple, `IComponent` (nom descriptif), `ICustomAttributeProvider` (expression nominale), et `IPersistable` (adjectif) sont des noms de l’interface appropriée. Comme avec d’autres noms de types, évitez d’abréviations.  
  
 **✓ FAIRE** vous assurer que les noms diffèrent uniquement par « I » du préfixe du nom de l’interface lorsque vous définissez une paire : interface de classe dans laquelle la classe est une implémentation standard de l’interface.  
  
## <a name="names-of-generic-type-parameters"></a>Noms des paramètres de Type générique  
 Les génériques ont été ajoutés à .NET Framework 2.0. La fonctionnalité introduit un nouveau type d’identificateur appelé *le paramètre de type*.  
  
 **✓ FAIRE** nom des paramètres de type générique avec des noms descriptifs, sauf si un nom de lettre unique est complètement explicite et un nom descriptif ajouterait pas de valeur.  
  
 **ENVISAGEZ de ✓** à l’aide de `T` comme nom de paramètre de type pour les types avec un paramètre de type de lettre unique.  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ FAIRE** préfixe des noms de paramètre de type descriptifs avec `T`.  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 **✓ Envisagez** indiquer les contraintes placées sur un paramètre de type dans le nom du paramètre.  
  
 Par exemple, un paramètre contraint à `ISession` peut être appelée `TSession`.  
  
## <a name="names-of-common-types"></a>Noms des Types courants  
 **✓ FAIRE** suivez les instructions décrites dans le tableau suivant lorsque vous nommez des types dérivés ou implémenter certains types .NET Framework.  
  
|Base Type|Règle de Type dérivé/de mise en œuvre|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ FAIRE** ajouter le suffixe « Attribute » aux noms des classes d’attributs personnalisés.|  
|`System.Delegate`|**✓ FAIRE** ajouter le suffixe « EventHandler » aux noms de délégués qui sont utilisés dans les événements.<br /><br /> **✓ FAIRE** ajouter le suffixe « Rappel » aux noms de délégués autres que ceux utilisés en tant que gestionnaires d’événements.<br /><br /> **X ne sont pas** ajouter le suffixe « Délégué » à un délégué.|  
|`System.EventArgs`|**✓ FAIRE** ajouter le suffixe « EventArgs ».|  
|`System.Enum`|**X ne sont pas** dériver de cette classe ; utilisez le mot clé pris en charge par votre langage à la place ; par exemple, en c#, utilisez le `enum` (mot clé).<br /><br /> **X ne sont pas** ajouter le suffixe « Enum » ou « Indicateur ».|  
|`System.Exception`|**✓ FAIRE** ajouter le suffixe « Exception ».|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ FAIRE** ajouter le suffixe « Dictionnaire ». Notez que `IDictionary` est un type spécifique de la collection, mais cette instruction est prioritaire sur la règle de collections plus générale qui suit.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ FAIRE** ajouter le suffixe « Collection ».|  
|`System.IO.Stream`|**✓ FAIRE** ajouter le suffixe « Stream ».|  
|`CodeAccessPermission IPermission`|**✓ FAIRE** ajouter le suffixe « Autorisation ».|  
  
## <a name="naming-enumerations"></a>Énumérations d’affectation de noms  
 Noms des types énumération (également appelés enums) en général doivent respecter les règles d’affectation de noms de type standard (casse Pascal, etc.). Toutefois, il existe des instructions supplémentaires qui s’appliquent spécifiquement aux enums.  
  
 **✓ FAIRE** utiliser un nom de type au singulier pour une énumération, sauf si ses valeurs sont les champs de bits.  
  
 **✓ FAIRE** utiliser un nom de type au pluriel pour une énumération avec les champs de bits sous forme de valeurs, également appelés enum d’indicateurs.  
  
 **X ne sont pas** utiliser le suffixe « Enum » dans les noms de type enum.  
  
 **X ne sont pas** utiliser « Indicateur » ou tapez les noms des suffixes « Indicateurs » dans l’enum.  
  
 **X ne sont pas** utiliser un préfixe sur les noms de valeur d’énumération (par exemple, « ad » pour les énumérations ADO.), « rtf » pour les énumérations de texte enrichi, etc.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Affectation de noms](../../../docs/standard/design-guidelines/naming-guidelines.md)
