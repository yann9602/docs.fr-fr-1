---
title: "Utilisation d&#39;indexeurs (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "indexeurs (C#), à propos des indexeurs"
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# Utilisation d&#39;indexeurs (Guide de programmation C#)
Les indexeurs vous permettent de créer facilement une [classe](../../../csharp/language-reference/keywords/class.md), un [struct](../../../csharp/language-reference/keywords/struct.md) ou une [interface](../../../csharp/language-reference/keywords/interface.md) auxquels les applications clientes peuvent accéder, tout comme un tableau.  Le plus souvent, les indexeurs sont implémentés dans les types dont l'objectif premier est d'encapsuler une collection ou un tableau interne.  Par exemple, supposons que votre classe TempRecord représente la température en Farenheit enregistrée à 10 moments différents au cours d'une période de 24 heures.  La classe contient un tableau de type float nommé « temps » pour représenter les températures et un <xref:System.DateTime> qui représente la date à laquelle les températures ont été enregistrées.  En implémentant un indexeur dans cette classe, les clients peuvent accéder aux températures dans une instance TempRecord sous la forme `float temp = tr[4]` au lieu de `float temp = tr.temps[4]`.  La notation d'indexeur simplifie non seulement la syntaxe pour les applications clientes, mais elle permet également aux autres développeurs de mieux comprendre l'objectif de la classe.  
  
 Pour déclarer un indexeur sur une classe ou un struct, utilisez le mot clé [this](../../../csharp/language-reference/keywords/this.md), comme dans l'exemple suivant :  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
  
```  
  
## Notes  
 Le type d'un indexeur et le type de ses paramètres doivent être au moins aussi accessibles que l'indexeur lui\-même.  Pour plus d'informations sur les niveaux d'accessibilité, consultez [Modificateurs d'accès](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Pour plus d'informations sur l'utilisation d'indexeurs avec une interface, consultez [Indexeurs d'interface](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).  
  
 La signature d'un indexeur est composée du nombre et des types de ses paramètres formels.  Elle n'inclut pas le type de l'indexeur ni les noms des paramètres formels.  Si vous déclarez plusieurs indexeurs dans la même classe, ils doivent avoir des signatures différentes.  
  
 Une valeur d'indexeur n'est pas classée en tant que variable ; vous ne pouvez donc pas la passer en tant que paramètre [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md).  
  
 Pour affecter à l'indexeur un nom exploitable dans d'autres langages, utilisez un attribut `name` dans la déclaration.  Par exemple :  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 Cet indexeur portera le nom `TheItem`.  Si vous ne précisez pas le nom de l'attribut, `Item` est pris comme nom par défaut.  
  
## Exemple 1  
  
### Description  
 L'exemple suivant montre comment déclarer un champ de tableau privé, `temps`, et un indexeur.  L'indexeur permet d'accéder directement à l'instance `tempRecord[i]`.  Comme alternative à l'utilisation de l'indexeur, vous pouvez déclarer le tableau en tant que membre [public](../../../csharp/language-reference/keywords/public.md)et accéder directement à ses membres, `tempRecord.temps[i]`.  
  
 Notez que lorsque l'accès à un indexeur est évalué, par exemple, dans une instruction `Console.Write`, l'accesseur [get](../../../csharp/language-reference/keywords/get.md) est appelé.  C'est pourquoi une erreur de compilation se produit si aucun accesseur `get` n'existe.  
  
### Code  
 [!code-cs[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## Indexation de l'utilisation d'autres valeurs  
 C\# ne limite pas les index au type entier.  Par exemple, il peut être utile d'utiliser une chaîne avec un indexeur.  Il est possible de l'implémenter en recherchant la chaîne dans la collection. La valeur appropriée est alors retournée.  Comme les accesseurs peuvent être surchargés, les versions chaîne et entier peuvent coexister.  
  
## Exemple 2  
  
### Description  
 Cet exemple déclare une classe stockant les jours de la semaine.  L'accesseur `get` déclaré prend une chaîne, le nom d'un jour, et retourne l'entier correspondant.  Par exemple, dimanche retourne 0, lundi retourne 1 et ainsi de suite.  
  
### Code  
 [!code-cs[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## Programmation fiable  
 La sécurité et la fiabilité des indexeurs peuvent être améliorées de deux manières principales :  
  
-   N'oubliez pas d'incorporer une stratégie de gestion des erreurs au cas où une valeur d'index non valide serait passée au code client.  Dans le premier exemple décrit plus haut, la classe TempRecord fournit une propriété Length qui permet au code client de vérifier l'entrée avant de la passer à l'indexeur.  Vous pouvez également placer le code de gestion des erreurs à l'intérieur de l'indexeur lui\-même.  N'oubliez pas d'indiquer aux utilisateurs toutes les exceptions que vous levez dans un accesseur d'indexeur.  
  
-   Définissez l'accessibilité des accesseurs `get` et [set](../../../csharp/language-reference/keywords/set.md) afin qu'elle soit aussi restrictive que possible.  C'est particulièrement important dans le cas de l'accesseur `set`.  Pour plus d'informations, consultez [Restriction d'accessibilité de l'accesseur](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Indexeurs](../../../csharp/programming-guide/indexers/index.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)