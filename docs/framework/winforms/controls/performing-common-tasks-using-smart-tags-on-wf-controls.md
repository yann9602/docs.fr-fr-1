---
title: "Proc&#233;dure pas &#224; pas&#160;: ex&#233;cution de t&#226;ches courantes &#224; l&#39;aide de balises actives dans les contr&#244;les Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "actions du concepteur"
  - "DesignerAction (modèle objet)"
  - "balises actives"
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Proc&#233;dure pas &#224; pas&#160;: ex&#233;cution de t&#226;ches courantes &#224; l&#39;aide de balises actives dans les contr&#244;les Windows Forms
Lorsque vous construisez des formulaires et des contrôles pour votre application Windows Forms, il existe de nombreuses tâches que vous effectuerez à plusieurs reprises.  Voici quelques\-unes des tâches courantes que vous aurez à exécuter :  
  
-   Ajout ou suppression d'un onglet sur un <xref:System.Windows.Forms.TabControl>.  
  
-   Ancrage d'un contrôle à son parent.  
  
-   Modification de l'orientation d'un contrôle <xref:System.Windows.Forms.SplitContainer>.  
  
 Pour accélérer le développement, beaucoup de contrôles offrent des balises actives qui sont des menus contextuels qui vous permettent d'exécuter des tâches courantes comme celles\-ci en un seul geste au moment du design.  Ces tâches sont appelées *verbes de balise active*.  
  
 Les balises actives restent attachées à une instance de contrôle pendant toute leur durée de vie dans le concepteur et sont toujours disponibles.  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Création d'un projet Windows Forms  
  
-   Utilisation de balises actives  
  
-   Activation et désactivation de balises actives  
  
 Lorsque vous aurez terminé, vous aurez assimilé le fonctionnement du rôle joué par ces importantes fonctionnalités de disposition.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Création du projet  
 La première étape consiste à créer le projet et configurer le formulaire.  
  
#### Pour créer le projet  
  
1.  Créez un projet d'application Windows appelé « SmartTagsExample ».  Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Sélectionnez le formulaire dans le **Concepteur Windows Forms**.  
  
## Utilisation des balises actives  
 Les balises actives sont toujours disponibles au moment du design sur les contrôles qui les proposent.  
  
#### Pour utiliser des balises actives  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TabControl> de la **Boîte à outils** jusqu'à votre formulaire.  Notez le glyphe de balise active \(![Glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) qui apparaît sur le côté du <xref:System.Windows.Forms.TabControl>.  
  
2.  Cliquez sur le glyphe de balise active.  Dans le menu contextuel qui apparaît à côté du glyphe, sélectionnez l'élément **Ajouter un onglet**.  Observez qu'une nouvelle page d'onglets est ajoutée au <xref:System.Windows.Forms.TabControl>.  
  
3.  Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **Boîte à outils** vers votre formulaire.  
  
4.  Cliquez sur le glyphe de balise active.  Dans le menu contextuel qui apparaît à côté du glyphe, sélectionnez l'élément **Ajouter une colonne**.  Observez qu'une nouvelle colonne est ajoutée au contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
5.  Faites glisser un contrôle <xref:System.Windows.Forms.SplitContainer> de la **Boîte à outils** vers votre formulaire.  
  
6.  Cliquez sur le glyphe de balise active.  Dans le menu contextuel qui apparaît à côté du glyphe, sélectionnez l'élément **Fractionnement horizontal**.  Observez que la barre de fractionnement du contrôle <xref:System.Windows.Forms.SplitContainer> est maintenant orientée horizontalement.  
  
## Voir aussi  
 <xref:System.Windows.Forms.TextBox>   
 <xref:System.Windows.Forms.TabControl>   
 <xref:System.Windows.Forms.SplitContainer>   
 <xref:System.ComponentModel.Design.DesignerActionList>   
 [Walkthrough: Adding Smart Tags to a Windows Forms Component](../Topic/Walkthrough:%20Adding%20Smart%20Tags%20to%20a%20Windows%20Forms%20Component.md)