---
title: "Noms de Classes, structures et Interfaces | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "noms de types, instructions"
  - "classes (.NET Framework), noms"
  - "énumérations (.NET Framework), noms"
  - "noms (.NET Framework), interfaces"
  - "noms de types communs"
  - "noms (.NET Framework), noms de types"
  - "noms de classes (.NET Framework),"
  - "interfaces (.NET Framework), noms"
  - "paramètres de type générique"
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# Noms de Classes, structures et Interfaces
Les instructions d’affectation de noms qui suivent s’appliquent aux noms de type général.  
  
 **✓ faire** nommez des classes et structures avec des noms ou des expressions nominales, à l’aide de la casse Pascal.  
  
 Cela la distingue les noms de types à partir de méthodes, qui sont nommées avec verbaux.  
  
 **✓ faire** nom interfaces expressions adjectives ou parfois avec des noms ou des expressions nominales.  
  
 Noms et des expressions nominales doivent être utilisées rarement et il peuvent indiquer que le type doit être une classe abstraite et non une interface.  
  
 **X ne pas** donner des noms de classe un préfixe \(par exemple, « C »\).  
  
 **✓ envisagez** se terminant par le nom de classes dérivées avec le nom de la classe de base.  
  
 Ceci est tout à fait lisible et explique la relation clairement. Voici quelques exemples de ce code : `ArgumentOutOfRangeException`, qui est un type de `Exception`, et `SerializableAttribute`, qui est un type de `Attribute`. Toutefois, il est important d’utiliser Réfléchissez soigneusement en appliquant cette indication ; par exemple, la `Button` classe est un type de `Control` événement, bien que `Control` n’apparaît pas dans son nom.  
  
 **✓ faire** noms d’interface de préfixe avec la lettre I pour indiquer que le type est une interface.  
  
 Par exemple, `IComponent` \(nom descriptif\), `ICustomAttributeProvider` \(nominal\) et `IPersistable` \(adjectif\) sont des noms d’interface appropriés. Comme avec les autres noms de types, évitez d’abréviations.  
  
 **✓ faire** vous assurer que les noms diffèrent uniquement par « I » du préfixe du nom de l’interface lorsque vous définissez une paire classe – interface où la classe est une implémentation standard de l’interface.  
  
## Noms des paramètres de Type générique  
 Les génériques ont été ajoutés à .NET Framework 2.0. La fonctionnalité introduit un nouveau type d’identificateur appelé *le paramètre de type*.  
  
 **✓ faire** nom des paramètres de type générique avec des noms descriptifs, sauf si un nom de lettre unique est complètement explicite et un nom descriptif n’apporte rien.  
  
 **✓ envisagez** à l’aide de `T` comme nom de paramètre de type pour les types ayant un paramètre de type de lettre unique.  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ faire** préfixe des noms de paramètre de type descriptifs avec `T`.  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 **✓ envisagez** indiquer les contraintes placées sur un paramètre de type dans le nom du paramètre.  
  
 Par exemple, un paramètre contraint à `ISession` peut être appelée `TSession`.  
  
## Noms des Types courants  
 **✓ faire** suivez les instructions décrites dans le tableau suivant lorsque vous nommez des types dérivés ou implémenter certains types .NET Framework.  
  
|Type de base|Règle de Type dérivé et l’implémentation|  
|------------------|----------------------------------------------|  
|`System.Attribute`|**✓ faire** ajouter le suffixe « Attribute » aux noms de classes d’attributs personnalisés. ajouter le suffixe « Attribute » aux noms de classes d’attributs personnalisés.|  
|`System.Delegate`|**✓ faire** ajouter le suffixe « EventHandler » aux noms des délégués qui sont utilisés dans les événements.<br /><br /> **✓ faire** ajouter le suffixe « Rappel » aux noms de délégués autres que ceux utilisés en tant que gestionnaires d’événements.<br /><br /> **X ne pas** ajouter le suffixe « Délégué » à un délégué.|  
|`System.EventArgs`|**✓ faire** ajouter le suffixe « EventArgs ».|  
|`System.Enum`|**X ne pas** dérivent de cette classe ; utilisez le mot clé pris en charge par votre langage plutôt ; par exemple, en c\#, utilisez le mot clé enum.<br /><br /> **X ne pas** ajouter le suffixe « Enum » ou « Indicateur ».|  
|`System.Exception`|**✓ faire** ajouter le suffixe « Exception ».|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ faire** ajouter le suffixe « Dictionnaire ». Notez que `IDictionary` est un type spécifique de collection, mais cette instruction est prioritaire sur la règle de collections plus générale qui suit.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ faire** ajouter le suffixe « Collection ».|  
|`System.IO.Stream`|**✓ faire** ajouter le suffixe « Stream ».|  
|`CodeAccessPermission IPermission`|**✓ faire** ajouter le suffixe « Autorisation ».|  
  
## Énumérations d’affectation de noms  
 Les noms des types énumération \(également appelées enums\) doivent en général suit les règles d’affectation de noms de type standard \(casse Pascal, etc.\). Toutefois, il existe des instructions supplémentaires qui s’appliquent spécifiquement aux énumérations.  
  
 **✓ faire** utilise un nom de type au singulier pour une énumération, sauf si ses valeurs sont des champs de bits.  
  
 **✓ faire** utiliser un nom de type au pluriel pour une énumération avec les champs de bits en tant que valeurs, également appelés énumération d’indicateurs.  
  
 **X ne pas** utiliser le suffixe « Enum » dans les noms de type enum.  
  
 **X ne pas** utiliser « Indicateur » ou les suffixes « Indicateurs » dans l’énumération des noms de types.  
  
 **X ne pas** utiliser un préfixe pour les noms de valeur \(énumération\) \(par exemple, « ad » pour les énumérations ADO.\), « format rtf » pour les énumérations de texte enrichi, etc..  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications concernant l'attribution d'un nom](../../../docs/standard/design-guidelines/naming-guidelines.md)