---
title: "Procédure pas à pas : exécution de tâches courantes à l’aide de balises actives dans les contrôles Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2e6b815be85576f037e0f24668c44756b95abd6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>Procédure pas à pas : exécution de tâches courantes à l’aide de balises actives dans les contrôles Windows Forms
Lorsque vous construisez des formulaires et les contrôles de votre application Windows Forms, il existe de nombreuses tâches, que vous allez effectuer à plusieurs reprises. Voici certaines des tâches courantes que vous rencontrerez :  
  
-   Ajout ou suppression d’un onglet sur un <xref:System.Windows.Forms.TabControl>.  
  
-   Ancrage d’un contrôle à son parent.  
  
-   Modification de l’orientation d’un <xref:System.Windows.Forms.SplitContainer> contrôle.  
  
 Pour accélérer le développement, de nombreux contrôles offrent des balises actives, qui sont des menus contextuels qui vous permettent d’effectuer des tâches courantes, comme dans un seul geste au moment du design. Ces tâches sont appelées *verbes de balise active*.  
  
 Balises actives restent attachées à une instance de contrôle pour sa durée de vie dans le concepteur et sont toujours disponibles.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un projet Windows Forms  
  
-   À l’aide de balises actives  
  
-   Activation et désactivation de balises actives  
  
 À l’issue de cette procédure, vous comprendrez le rôle joué par ces fonctionnalités de disposition importantes.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer le projet et à configurer le formulaire.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Créez un projet d’application Windows appelé « SmartTagsExample ». Pour plus d’informations, consultez l’article [Comment : créer un projet d’application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Sélectionnez le formulaire dans le **Concepteur Windows Forms**.  
  
## <a name="using-smart-tags"></a>À l’aide de balises actives  
 Les balises actives sont toujours disponibles au moment du design sur les contrôles qui les proposent.  
  
#### <a name="to-use-smart-tags"></a>Pour utiliser des balises actives  
  
1.  Faites glisser un <xref:System.Windows.Forms.TabControl> à partir de la **boîte à outils** vers votre formulaire. Notez le glyphe de balise active (![glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) qui apparaît sur le côté de la <xref:System.Windows.Forms.TabControl>.  
  
2.  Cliquez sur le glyphe de balise active. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez le **ajouter un onglet** élément. Observez qu’une nouvelle page d’onglet est ajoutée à la <xref:System.Windows.Forms.TabControl>.  
  
3.  Faites glisser un <xref:System.Windows.Forms.TableLayoutPanel> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
4.  Cliquez sur le glyphe de balise active. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez le **ajouter une colonne** élément. Observez qu’une nouvelle colonne est ajoutée à la <xref:System.Windows.Forms.TableLayoutPanel> contrôle.  
  
5.  Faites glisser un <xref:System.Windows.Forms.SplitContainer> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
6.  Cliquez sur le glyphe de balise active. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez le **fractionnement Horizontal** élément. Observez que le <xref:System.Windows.Forms.SplitContainer> barre de fractionnement du contrôle est maintenant orientée horizontalement.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [Procédure pas à pas : Ajout de balises actives pour un composant Windows Forms](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
