---
title: "Avantages des g&#233;n&#233;riques (guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "génériques (C#), avantages"
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avantages des g&#233;n&#233;riques (guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les génériques offrent la solution à une limitation dans les versions antérieures du common language runtime et du langage C\# dans lesquels la généralisation s'effectue par casting des types vers et depuis le type de base universel <xref:System.Object>.  En créant une classe générique, vous pouvez créer une collection qui est de type sécurisé au moment de la compilation.  
  
 Les restrictions relatives à l'utilisation de classes de collections non génériques peuvent être illustrées par l'écriture d'un programme court qui utilise la classe de collection <xref:System.Collections.ArrayList> de la bibliothèque de classes .NET Framework.  <xref:System.Collections.ArrayList> est une classe de collection très pratique qui peut être utilisée sans modification pour stocker tout type référence ou valeur.  
  
 [!code-cs[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]  
  
 Mais cette commodité a un coût.  Tout type référence ou valeur qui est ajouté à un <xref:System.Collections.ArrayList> est implicitement upcasté en <xref:System.Object>.  Si les éléments sont des types valeur, ils doivent faire l'objet d'un boxing lorsqu'ils sont ajoutés à la liste, et d'un unboxing lorsqu'ils sont récupérés.  Les opérations de casting et de boxing \/ unboxing affectent les performances. L'effet du boxing et de l'unboxing peut être très significatif lorsque vous itérez au sein de collections très volumineuses.  
  
 L'autre limitation réside dans le manque de vérification de type compilation. Puisqu'un <xref:System.Collections.ArrayList> effectue un cast de tout en <xref:System.Object>, il n'existe aucun moyen à la compilation d'empêcher le code client de procéder comme suit :  
  
 [!code-cs[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]  
  
 Bien que parfaitement acceptable et parfois intentionnelle si vous créez une collection hétérogène, la combinaison de chaînes et d'entiers \(`ints`\) dans une seule <xref:System.Collections.ArrayList> est plus vraisemblablement une erreur de programmation, et cette erreur ne sera pas détectée avant l'exécution.  
  
 Dans les versions 1.0 et 1.1 du langage C\#, le seul moyen d'éviter les dangers du code généralisé dans les classes de collections de bibliothèques de classes de base .NET Framework était d'écrire vos propres collections spécifiques à un type.  Bien sûr, puisqu'une classe de ce genre n'est pas réutilisable pour plusieurs types de données, vous perdez les avantages de la généralisation, et vous devez réécrire la classe pour chaque type qui sera stocké.  
  
 Ce dont <xref:System.Collections.ArrayList> et d'autres classes semblables ont vraiment besoin est un moyen permettant au code client de spécifier, pour chaque instance, le type de données particulier qu'elles ont l'intention d'utiliser.  Cela éviterait la nécessité de devoir effectuer un upcast en `T:System.Object` et permettrait également au compilateur d'effectuer un contrôle de type.  En d'autres termes, <xref:System.Collections.ArrayList> a besoin d'un paramètre de type.  C'est exactement ce que les génériques assurent.  Dans la collection <xref:System.Collections.Generic.List%601> générique, dans l'espace de noms `N:System.Collections.Generic`, la même opération d'ajout d'éléments à la collection ressemble à ceci :  
  
 [!code-cs[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]  
  
 Pour le code client, la seule syntaxe ajoutée avec <xref:System.Collections.Generic.List%601> comparée à <xref:System.Collections.ArrayList> est l'argument de type dans la déclaration et l'instanciation.  En échange de cette complexité de codage légèrement supérieure, vous pouvez créer une liste qui est non seulement plus sûre que <xref:System.Collections.ArrayList>, mais également considérablement plus rapide, surtout lorsque les éléments de la liste sont des types valeur.  
  
## Voir aussi  
 <xref:System.Collections.Generic>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Conversion boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)   
 [Meilleures pratiques de collections](http://go.microsoft.com/fwlink/?LinkId=112403)