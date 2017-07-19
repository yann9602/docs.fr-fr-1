---
title: "Comment&#160;: utiliser les modificateurs et les propri&#233;t&#233;s GenerateMember | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_GenerateMember"
  - "Designer_Modifiers"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "formulaires de base"
  - "héritage de formulaire"
  - "GenerateMember (propriété)"
  - "héritage, formulaires"
  - "formulaires hérités"
  - "formulaires hérités, Windows Forms"
  - "Modifiers (propriété)"
  - "Windows Forms, héritage"
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: utiliser les modificateurs et les propri&#233;t&#233;s GenerateMember
Lorsque vous placez un composant sur un Windows Form, deux propriétés sont fournies par l'environnement de design : `GenerateMember` et `Modifiers`.  La propriété `GenerateMember` spécifie à quel moment le Concepteur Windows Forms génère une variable membre pour un composant.  La propriété `Modifiers` est le modificateur d'accès assigné à cette variable membre.  Si la valeur de la propriété `GenerateMember` est `false`, la valeur de la propriété `Modifiers` n'a aucun effet.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour spécifier si un composant est un membre du formulaire  
  
1.  Dans le Concepteur Windows Forms, ouvrez votre formulaire.  
  
2.  Ouvrez la **boîte à outils** et, sur le formulaire, placez trois contrôles <xref:System.Windows.Forms.Button>.  
  
3.  Définissez les propriétés `GenerateMember` et `Modifiers` pour chaque contrôle <xref:System.Windows.Forms.Button> d'après le tableau suivant.  
  
    |Nom du bouton|Valeur de GenerateMember|Valeur de Modifiers|  
    |-------------------|------------------------------|-------------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|Aucune modification|  
  
4.  Générez la solution.  
  
5.  Dans l'**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.  
  
6.  Ouvrez le nœud **Form1**, puis dans l'**éditeur de code**, ouvrez le fichier **Form1.Designer.vb** ou **Form1.Designer.cs**.  Ce fichier contient le code émis par le Concepteur Windows Forms.  
  
7.  Recherchez les déclarations pour les trois boutons.  L'exemple de code suivant montre les différences spécifiées par les propriétés `GenerateMember` et `Modifiers`.  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  Par défaut, le Concepteur Windows Forms assigne le modificateur `private` \(`Friend` en Visual Basic\) aux contrôles conteneur comme <xref:System.Windows.Forms.Panel>.  Si votre <xref:System.Windows.Forms.Form> ou <xref:System.Windows.Forms.UserControl> de base a un contrôle conteneur, il n'acceptera pas de nouveaux enfants dans les formulaires et contrôles hérités.  La solution consiste à changer le modificateur du contrôle conteneur de base en `protected` ou `public`.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Button>   
 [Héritage visuel des Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)   
 [Procédure pas à pas : démonstration de l'héritage visuel](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)   
 [Comment : hériter des Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)