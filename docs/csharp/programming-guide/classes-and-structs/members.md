---
title: "Membres (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, membres de type"
  - "types (C#), types imbriqués"
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# Membres (Guide de programmation C#)
Les classes et structs ont des membres qui représentent leurs données et comportement.  Les membres d'une classe incluent tous les membres déclarés dans la classe, avec tous les membres \(excepté les constructeurs et les destructeurs\) déclarés dans toutes les classes dans leur hiérarchie d'héritage.  Les membres privés dans les classes de base sont hérités mais ne sont pas accessibles à partir de classes dérivées.  
  
 Le tableau suivant répertorie les types de membres qu'une classe ou un struct peut contenir :  
  
|Membre|Description|  
|------------|-----------------|  
|[Champs](../../../csharp/programming-guide/classes-and-structs/fields.md)|Les champs sont des variables déclarées dans la portée de la classe.  Un champ peut être un type numérique intégré ou une instance d'une autre classe.  Par exemple, une classe de calendrier peut avoir un champ qui contient la date courante.|  
|[Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)|Les constantes sont des champs ou des propriétés dont la valeur est définie à la compilation et n'est pas modifiable.|  
|[Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)|Les propriétés sont des méthodes sur une classe auxquelles on accède comme s'il s'agissait de champs sur cette classe.  Une propriété peut protéger un champ de classe pour éviter qu'il soit modifié sans connaissance de l'objet.|  
|[Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)|Les méthodes définissent les actions qu'une classe peut effectuer.  Les méthodes peuvent employer des paramètres qui fournissent les données d'entrée et retourner des données de sortie via des paramètres.  Les méthodes peuvent également retourner une valeur directement, sans utiliser de paramètre.|  
|[Événements](../../../csharp/programming-guide/events/index.md)|Les événements fournissent des notifications sur les occurrences telles que des clics de bouton ou l'aboutissement d'une méthode, à d'autres objets.  Les événements sont définis et déclenchés à l'aide de délégués.|  
|[Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Les opérateurs surchargés sont considérés comme des membres de classe.  Lorsque vous surchargez un opérateur, vous le définissez comme une méthode statique publique dans une classe.  Les opérateurs prédéfinis \(`+`, `*``<`, et ainsi de suite\) ne sont pas considérés comme membres.  Pour plus d'informations, consultez [Opérateurs surchargeables](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md).|  
|[Indexeurs](../../../csharp/programming-guide/indexers/index.md)|Les indexeurs permettent à un objet d'être indexé d'une manière semblable aux tableaux.|  
|[Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Les constructeurs sont des méthodes qui sont appelées lors de la création de l'objet.  Ils sont souvent utilisés pour initialiser les données d'un objet.|  
|[Destructeurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)|Les destructeurs sont très rarement utilisés en C\#.  Ce sont des méthodes qui sont appelées par le moteur d'exécution lorsque l'objet est sur le point d'être supprimé de la mémoire.  Ils sont généralement utilisés pour s'assurer que toutes les ressources qui doivent être libérées sont gérées de manière appropriée.|  
|[Types imbriqués](../../../csharp/programming-guide/classes-and-structs/nested-types.md)|Les types imbriqués sont des types déclarés dans un autre type.  Les types imbriqués sont souvent utilisés pour décrire des objets utilisés uniquement par les types qui les contiennent.|  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Destructeurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Champs](../../../csharp/programming-guide/classes-and-structs/fields.md)   
 [Indexeurs](../../../csharp/programming-guide/indexers/index.md)   
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [Types imbriqués](../../../csharp/programming-guide/classes-and-structs/nested-types.md)   
 [Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)   
 [Opérateurs surchargeables](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)