---
title: "Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dce58776af84b1f4c733ddce2553e4b18b1b824
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a>Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize
Le positionnement précis des contrôles sur votre formulaire constitue une haute priorité pour de nombreuses applications. Le **Concepteur Windows Forms** vous offre de nombreux outils de disposition pour y parvenir. Trois des plus importants sont les <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, et <xref:System.Windows.Forms.Control.AutoSize%2A> propriétés, qui sont présentes sur tous les contrôles Windows Forms.  
  
 La propriété <xref:System.Windows.Forms.Control.Margin%2A> définit l'espace autour du contrôle qui maintient les autres contrôles à une distance spécifiée des bordures du contrôle.  
  
 La propriété <xref:System.Windows.Forms.Control.Padding%2A> définit l'espace à l'intérieur d'un contrôle qui maintient le contenu du contrôle (par exemple la valeur de sa propriété <xref:System.Windows.Forms.Control.Text%2A>) à une distance spécifiée des bordures du contrôle.  
  
 L'illustration suivante montre les propriétés <xref:System.Windows.Forms.Control.Padding%2A> et <xref:System.Windows.Forms.Control.Margin%2A> d'un contrôle.  
  
 ![Remplissage et marge pour les Windows Forms contrôles](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 Le <xref:System.Windows.Forms.Control.AutoSize%2A> propriété indique à un contrôle se redimensionne automatiquement à son contenu. Il n’est pas redimensionné automatiquement pour être plus petite que la valeur de son état d’origine <xref:System.Windows.Forms.Control.Size%2A> propriété et il représentera la valeur de son <xref:System.Windows.Forms.Control.Padding%2A> propriété.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un projet Windows Forms  
  
-   Définition des marges de vos contrôles  
  
-   Définition du remplissage de vos contrôles  
  
-   Dimensionnement automatique de vos contrôles  
  
 À l’issue de cette procédure, vous comprendrez le rôle joué par ces fonctionnalités de disposition importantes.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Autorisations suffisantes pour pouvoir créer et exécuter des projets d’application Windows Forms sur l’ordinateur où Visual Studio est installé.  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer le projet et à configurer le formulaire.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Créer un **Application Windows** projet appelé `LayoutExample`. Pour plus d’informations, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) .  
  
2.  Sélectionnez le formulaire dans le **Concepteur Windows Forms**.  
  
## <a name="setting-margins-for-your-controls"></a>Définition des marges de vos contrôles  
 Vous pouvez définir la distance par défaut entre vos contrôles à l’aide de la <xref:System.Windows.Forms.Control.Margin%2A> propriété. Lorsque vous déplacez un contrôle suffisamment proches d’un autre contrôle, vous verrez une ligne d’alignement qui affiche les marges pour les deux contrôles. Le contrôle que vous déplacez s’alignera également à la distance définie par les marges.  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a>Pour réorganiser des contrôles sur votre formulaire à l’aide de la propriété Margin  
  
1.  Faites glisser deux <xref:System.Windows.Forms.Button> des contrôles de la **boîte à outils** vers votre formulaire.  
  
2.  Sélectionnez une de le <xref:System.Windows.Forms.Button> contrôle et déplacez-le proche de l’autre, jusqu'à ce qu’ils se touchent presque.  
  
     Observez la ligne d’alignement qui apparaît entre eux. Cette distance est la somme des deux contrôles <xref:System.Windows.Forms.Control.Margin%2A> valeurs. Le contrôle que vous déplacez s’aligne sur cette distance. Pour plus d’informations, consultez [procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
3.  Modifier la <xref:System.Windows.Forms.Control.Margin%2A> propriété de l’un des contrôles en développant le <xref:System.Windows.Forms.Control.Margin%2A> entrée dans le **propriétés** fenêtre et en attribuant le <xref:System.Windows.Forms.Padding.All%2A> propriété à 20.  
  
4.  Sélectionnez une de le <xref:System.Windows.Forms.Button> contrôle et déplacez-le proche de l’autre.  
  
     La ligne d’alignement définit la somme des valeurs de marge est plus longue et que le contrôle s’aligne à une distance supérieure à partir de l’autre contrôlent.  
  
5.  Modifier la <xref:System.Windows.Forms.Control.Margin%2A> propriété du contrôle sélectionné en développant le <xref:System.Windows.Forms.Control.Margin%2A> entrée dans le **propriétés** fenêtre et en attribuant le <xref:System.Windows.Forms.Padding.Top%2A> propriété à 5.  
  
6.  Déplace le contrôle sélectionné sous l’autre contrôle et notez que la ligne d’alignement est plus court. Déplacer le contrôle sélectionné à gauche de l’autre contrôle et observez que la ligne d’alignement conserve la valeur observée à l’étape 4.  
  
7.  Vous pouvez définir chacun des aspects de la <xref:System.Windows.Forms.Control.Margin%2A> propriété, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, pour des valeurs différentes, ou vous peut affecter tous la même valeur avec le <xref:System.Windows.Forms.Padding.All%2A> propriété.  
  
## <a name="setting-padding-for-your-controls"></a>Définition du remplissage de vos contrôles  
 Pour obtenir la disposition précise requise pour votre application, vos contrôles contient souvent des contrôles enfants. Lorsque vous souhaitez spécifier la proximité de bordure du contrôle de l’enfant à la bordure du contrôle de parent, utilisez du contrôle parent <xref:System.Windows.Forms.Control.Padding%2A> propriété conjointement avec le contrôle d’enfant <xref:System.Windows.Forms.Control.Margin%2A> propriété. Le <xref:System.Windows.Forms.Control.Padding%2A> propriété est également utilisée pour contrôler la proximité du contenu d’un contrôle (par exemple, un <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Text%2A> propriété) à ses bordures.  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a>Pour réorganiser des contrôles sur votre formulaire à l’aide du remplissage  
  
1.  Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
2.  Affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Button>.  
  
3.  Modifier la <xref:System.Windows.Forms.Control.Padding%2A> propriété en développant le <xref:System.Windows.Forms.Control.Padding%2A> entrée dans le **propriétés** fenêtre et en attribuant le <xref:System.Windows.Forms.Padding.All%2A> propriété à 5.  
  
     Le contrôle se développe pour fournir l’espace pour le nouveau remplissage.  
  
4.  Faites glisser un <xref:System.Windows.Forms.GroupBox> contrôle depuis la **boîte à outils** vers votre formulaire. Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** dans le <xref:System.Windows.Forms.GroupBox> contrôle. Position du <xref:System.Windows.Forms.Button> contrôler par conséquent, il est aligné sur le coin inférieur droit de la <xref:System.Windows.Forms.GroupBox> contrôle.  
  
     Observez les lignes d’alignement apparaissent en tant que le <xref:System.Windows.Forms.Button> contrôle s’approche des bordures inférieure et droite de la <xref:System.Windows.Forms.GroupBox> contrôle. Ces lignes d’alignement correspondent à la <xref:System.Windows.Forms.Control.Margin%2A> propriété de la <xref:System.Windows.Forms.Button>.  
  
5.  Modifier la <xref:System.Windows.Forms.GroupBox> du contrôle <xref:System.Windows.Forms.Control.Padding%2A> propriété en développant le <xref:System.Windows.Forms.Control.Padding%2A> entrée dans le **propriétés** fenêtre et en attribuant le <xref:System.Windows.Forms.Padding.All%2A> propriété à 20.  
  
6.  Sélectionnez le <xref:System.Windows.Forms.Button> contrôler dans le <xref:System.Windows.Forms.GroupBox> de contrôle et déplacez-le vers le centre de la <xref:System.Windows.Forms.GroupBox>.  
  
     Les lignes d’alignement apparaissent à une distance supérieure des bordures de la <xref:System.Windows.Forms.GroupBox> contrôle. Cette distance est la somme de la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Margin%2A> propriété et la <xref:System.Windows.Forms.GroupBox> du contrôle <xref:System.Windows.Forms.Control.Padding%2A> propriété.  
  
## <a name="automatically-sizing-your-controls"></a>Dimensionnement automatique de vos contrôles  
 Dans certaines applications, la taille d’un contrôle non sera le même en cours d’exécution tel qu’il était au moment du design. Le texte d’un <xref:System.Windows.Forms.Button> (contrôle), par exemple, peut-être être pris à partir d’une base de données, et sa longueur n’est pas connue à l’avance.  
  
 Lorsque le <xref:System.Windows.Forms.Control.AutoSize%2A> est définie sur `true`, le contrôle ajuste sa taille à son contenu. Pour plus d’informations, consultez [vue d’ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a>Pour réorganiser des contrôles sur votre formulaire à l’aide de la propriété AutoSize  
  
1.  Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
2.  Affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Button>.  
  
3.  Modifier la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Text%2A> propriété »**ce bouton a une longue chaîne pour sa propriété Text**. »  
  
     Lorsque vous validez la modification, la <xref:System.Windows.Forms.Button> contrôle se redimensionne pour contenir le nouveau texte.  
  
4.  Faites glisser une autre <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
5.  Modifier la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Text%2A> propriété »**ce bouton a une longue chaîne pour sa propriété Text.**»  
  
     Lorsque vous validez la modification, la <xref:System.Windows.Forms.Button> contrôle ne se redimensionne pas, et le texte est tronqué par le bord droit du contrôle.  
  
6.  Modifier la <xref:System.Windows.Forms.Control.Padding%2A> propriété en développant le <xref:System.Windows.Forms.Control.Padding%2A> entrée dans le **propriétés** fenêtre et en attribuant le <xref:System.Windows.Forms.Padding.All%2A> propriété à 5.  
  
     Le texte de l’intérieur du contrôle est découpé sur les quatre côtés.  
  
7.  Modifier la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.AutoSize%2A> propriété `true`.  
  
     Le <xref:System.Windows.Forms.Button> contrôle se redimensionne pour contenir la chaîne entière. En outre, le remplissage a été ajouté autour du texte, à l’origine de la <xref:System.Windows.Forms.Button> contrôle à développer dans les quatre directions.  
  
8.  Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** vers votre formulaire. Placez-le près de l’angle inférieur droit du formulaire.  
  
9. Affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Button>.  
  
10. Définir le <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Anchor%2A> propriété <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.  
  
11. Modifier la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Text%2A> propriété »**ce bouton a une longue chaîne pour sa propriété Text.**»  
  
     Lorsque vous validez la modification, la <xref:System.Windows.Forms.Button> contrôle redimensionne vers la gauche. En général, le dimensionnement automatique augmente la taille d’un contrôle dans le sens opposé son <xref:System.Windows.Forms.Control.Anchor%2A> paramètre de propriété.  
  
## <a name="autosize-and-autosizemode-properties"></a>Propriétés AutoSize et AutoSizeMode  
 Certains contrôles prennent en charge le `AutoSizeMode` propriété, ce qui vous donne un contrôle plus précis sur le comportement de dimensionnement automatique d’un contrôle.  
  
#### <a name="to-use-the-autosizemode-property"></a>Pour utiliser la propriété AutoSizeMode  
  
1.  Faites glisser un <xref:System.Windows.Forms.Panel> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
2.  Définir la valeur de la <xref:System.Windows.Forms.Panel> du contrôle <xref:System.Windows.Forms.Control.AutoSize%2A> propriété `true`.  
  
3.  Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** dans le <xref:System.Windows.Forms.Panel> contrôle.  
  
4.  Place le <xref:System.Windows.Forms.Button> contrôle dans l’angle inférieur droit de la <xref:System.Windows.Forms.Panel> contrôle.  
  
5.  Sélectionnez le <xref:System.Windows.Forms.Panel> contrôler et saisissez la poignée de redimensionnement inférieure droite. Redimensionner le <xref:System.Windows.Forms.Panel> contrôle soit supérieure et inférieure.  
  
    > [!NOTE]
    >  Vous pouvez redimensionner librement le <xref:System.Windows.Forms.Panel> contrôle, mais vous ne pouvez pas rendre plus petit que la position de la <xref:System.Windows.Forms.Button> bas à droite du contrôle. Ce comportement est spécifié par la valeur par défaut de la `AutoSizeMode` propriété, qui est <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.  
  
6.  Définir la valeur de la <xref:System.Windows.Forms.Panel> du contrôle `AutoSizeMode` propriété <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.  
  
     Le <xref:System.Windows.Forms.Panel> contrôle se redimensionne autour du <xref:System.Windows.Forms.Button> contrôle. Vous ne pouvez pas redimensionner la <xref:System.Windows.Forms.Panel> contrôle.  
  
7.  Faites glisser le <xref:System.Windows.Forms.Button> contrôle vers le coin supérieur gauche de la <xref:System.Windows.Forms.Panel> contrôle.  
  
     Le <xref:System.Windows.Forms.Panel> contrôle est redimensionné à la <xref:System.Windows.Forms.Button> nouvelle position du contrôle.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Il existe de nombreuses autres fonctionnalités de disposition pour organiser les contrôles dans vos applications Windows Forms. Voici certaines combinaisons que vous pouvez essayer :  
  
-   Créez un formulaire avec un <xref:System.Windows.Forms.TableLayoutPanel> contrôle. Pour plus d’informations, consultez [procédure pas à pas : organisation des contrôles dans les formulaires Windows à l’aide d’un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Essayez de modifier les valeurs de la <xref:System.Windows.Forms.TableLayoutPanel> du contrôle <xref:System.Windows.Forms.Control.Padding%2A> propriété, ainsi que le <xref:System.Windows.Forms.Control.Margin%2A> propriété sur ses contrôles enfants.  
  
-   Utilisez la même expérience un <xref:System.Windows.Forms.FlowLayoutPanel> contrôle. Pour plus d’informations, consultez [procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
-   Essayez d’ancrer des contrôles enfants dans un <xref:System.Windows.Forms.Panel> contrôle. Le <xref:System.Windows.Forms.Control.Padding%2A> propriété est une réalisation plus générale de la <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> propriété et que vous pouvez répondre aux vous-même que c’est le cas en mettant un contrôle enfant dans un <xref:System.Windows.Forms.Panel> contrôle et la définition du contrôle enfant <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Fill>. Définir le <xref:System.Windows.Forms.Panel> du contrôle <xref:System.Windows.Forms.Control.Padding%2A> propriété différentes valeurs et notez l’effet.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 [Vue d’ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
