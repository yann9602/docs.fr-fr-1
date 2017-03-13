---
title: "Exemple de classe COM (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "COM, exposer des objets Visual C# à"
  - "exemples (C#), Classes COM"
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# Exemple de classe COM (Guide de programmation C#)
Ci\-dessous un exemple d'une classe que vous exposeriez comme un objet COM.  Une fois que le code a été placé dans un fichier .cs et ajouté à votre projet, attribuez la valeur **True** à la propriété **Inscrire pour COM Interop**.  Pour plus d'informations, consultez [NIB: How to: Register a Component for COM Interop](http://msdn.microsoft.com/fr-fr/4de7d474-56e8-4027-994d-d47ca4725c5e).  
  
 L'exposition d'objets Visual C\# à COM requiert la déclaration d'une interface de classe, d'une interface d'événement, si elle est requise, et de la classe elle\-même.  Les membres de la classe doivent se conformer aux règles suivantes pour être visibles par COM :  
  
-   La classe doit être publique.  
  
-   Les propriétés, les méthodes et les événements doivent être publics.  
  
-   Les propriétés et les méthodes doivent être déclarées sur l'interface de classe.  
  
-   Les événements doivent être déclarés dans l'interface d'événements.  
  
 Les autres membres publics de la classe qui ne sont pas déclarés dans ces interfaces ne seront pas visibles pour COM, mais seront visibles pour d'autres objets .NET Framework.  
  
 Pour exposer des propriétés et des méthodes à COM, vous devez les déclarer dans l'interface de classe, les marquer avec l'attribut `DispId` et les implémenter dans la classe.  L'ordre dans lequel les membres sont déclarés dans l'interface est l'ordre utilisé pour la vtable COM.  
  
 Pour exposer des événements à partir de votre classe, vous devez les déclarer sur l'interface d'événements et les marquer avec un attribut `DispId`.  La classe ne doit pas implémenter cette interface.  
  
 La classe implémente l'interface de classe \(elle peut implémenter plus d'une interface, mais la première implémentation sera l'interface de classe par défaut\).  Implémentez les méthodes et les propriétés exposées à COM à cet emplacement.  Ces propriétés et méthodes doivent être marquées comme publiques et doivent correspondre aux déclarations de l'interface de classe.  Déclarez également les événements déclenchés par la classe à cet emplacement.  Ils doivent être marqués comme publics et doivent correspondre aux déclarations dans l'interface d'événement.  
  
## Exemple  
 [!code-cs[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Interopérabilité](../../../csharp/programming-guide/interop/interoperability.md)   
 [Générer, page du Concepteur de projets \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp)