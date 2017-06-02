---
title: "Erreurs au moment du design dans le Concepteur Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DTELErrorList"
  - "WhyDTELPage"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "erreurs au moment du design (Concepteur Windows Forms)"
  - "erreurs (Concepteur Windows Forms)"
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Erreurs au moment du design dans le Concepteur Windows Forms
Cette rubrique explique la signification et l'utilisation de la liste d'erreurs au moment du design qui apparaît dans Microsoft Visual Studio lorsque le chargement du Concepteur Windows Forms échoue.  Si cette liste d'erreurs apparaît, vous ne devez pas l'interpréter comme un bogue dans le concepteur, mais comme une aide pour corriger des erreurs dans votre code.  
  
 Une compréhension des notions fondamentales de cette liste d'erreurs vous aidera à déboguer vos applications, en fournissant des informations détaillées sur les erreurs et en suggérant les solutions possibles.  
  
## Interface de la liste d'erreurs au moment du design  
 Si le chargement du concepteur Windows Forms échoue, une liste d'erreurs apparaît dans le concepteur.  Les erreurs sont regroupées en catégories.  Par exemple, si vous avez quatre instances de variables non déclarées, celles\-ci seront regroupées dans la même catégorie d'erreur.  Chaque catégorie d'erreur inclut une brève description qui résume l'erreur.  
  
 Vous pouvez développer ou réduire une catégorie d'erreur en cliquant sur l'en\-tête de la catégorie d'erreur ou sur le chevron développer\/réduire.  Lorsque vous développez une catégorie d'erreur, l'aide supplémentaire suivante s'affiche :  
  
-   Instances de cette erreur.  
  
-   Aide sur cette erreur.  
  
-   Publications du forum sur cette erreur.  
  
### Instances de cette erreur  
 L'aide supplémentaire répertorie toutes les instances de l'erreur dans votre projet actuel.  De nombreuses erreurs incluent un emplacement exact dans le format suivant : *\[nom du projet\]* *\[nom du formulaire\]* Ligne :*\[numéro de la ligne\]* Colonne :*\[numéro de la colonne\]*.  Le lien **Accéder au code** vous conduit à l'emplacement dans votre code où l'erreur se produit.  
  
 Si une pile d'appel est associée à l'erreur, vous pouvez cliquer sur le lien **Afficher la pile des appels**, qui permet de développer davantage l'erreur afin d'afficher la pile d'appel.  L'examen de la pile peut fournir des informations de débogage précieuses.  Par exemple, vous pouvez suivre les fonctions appelées avant que l'erreur ne se produise.  La pile d'appel peut être sélectionnée afin que vous puissiez la copier et l'enregistrer.  
  
> [!NOTE]
>  Dans Visual Basic, la liste d'erreurs au moment du design n'affiche pas plus d'une erreur, mais elle peut afficher plusieurs instances de la même erreur.  Dans Visual C\+\+, les erreurs n'ont pas de liens d'accès au code ou de liens vers un numéro de ligne.  
  
### Aide sur cette erreur  
 Si l'erreur contient un lien vers une rubrique d'aide MSDN associée, l'aide supplémentaire inclut un lien vers la rubrique d'aide.  Lorsque vous cliquez sur le lien, la rubrique d'aide associée apparaît dans Visual Studio.  
  
### Publications du forum sur cette erreur  
 L'aide supplémentaire inclut un lien vers les publications du forum MSDN relatives à l'erreur.  Les forums sont recherchés selon la chaîne du message d'erreur.  Vous pouvez également essayer de rechercher dans les forums suivants :  
  
-   [Forum Windows Forms Designer \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [Forums Windows Forms \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=203523)  
  
### Ignorer et continuer  
 Vous pouvez choisir d'ignorer la condition d'erreur et continuer à charger le concepteur.  Le choix de cette action peut provoquer un comportement inattendu.  Par exemple, les contrôles peuvent ne pas apparaître sur l'aire de conception.  
  
## Voir aussi  
 [Troubleshooting Design\-Time Development](../Topic/Troubleshooting%20Design-Time%20Development.md)   
 [Dépannage de la création de contrôles et de composants](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)   
 [Développement de contrôles Windows Forms au moment du design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)   
 [Windows Forms Designer Error Messages](http://msdn.microsoft.com/fr-fr/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)