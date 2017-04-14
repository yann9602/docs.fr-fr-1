---
title: "Proc&#233;dure pas &#224; pas&#160;: disposition des contr&#244;les Windows Forms avec les propri&#233;t&#233;s Padding, Margins et AutoSize | Microsoft Docs"
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
  - "Margin.Bottom"
  - "Margin.Left"
  - "Margin.Top"
  - "Margin.All"
  - "Margin.Right"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "AutoSize (propriété), procédures pas à pas"
  - "disposition (Windows Forms), marges et marge intérieure"
  - "Margin (propriété Windows Forms), procédures pas à pas"
  - "Padding (propriété Windows Forms), procédures pas à pas"
  - "procédures pas à pas (Windows Forms), disposition"
  - "Windows Forms, disposition"
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 28
---
# Proc&#233;dure pas &#224; pas&#160;: disposition des contr&#244;les Windows Forms avec les propri&#233;t&#233;s Padding, Margins et AutoSize
Le positionnement précis des contrôles sur votre formulaire est une haute priorité pour beaucoup d'applications.  Le **Concepteur Windows Forms** vous donne beaucoup d'outils de disposition et de mise en page pour accomplir cette opération.  Trois des plus importants sont les propriétés suivantes : <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A> et <xref:System.Windows.Forms.Control.AutoSize%2A>, qui sont présentes sur tous les contrôles Windows Forms.  
  
 La propriété <xref:System.Windows.Forms.Control.Margin%2A> définit l'espace autour du contrôle que garde d'autres contrôles à une distance spécifiée des bordures du contrôle.  
  
 La propriété <xref:System.Windows.Forms.Control.Padding%2A> définit l'espace à l'intérieur d'un contrôle que garde le contenu du contrôle \(par exemple, la valeur de sa propriété <xref:System.Windows.Forms.Control.Text%2A>\) à une distance spécifiée des bordures du contrôle.  
  
 L'illustration suivante montre les propriétés <xref:System.Windows.Forms.Control.Padding%2A> et <xref:System.Windows.Forms.Control.Margin%2A> sur un contrôle.  
  
 ![Remplissage et marge pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS\_WinFormPadMargin")  
  
 La propriété <xref:System.Windows.Forms.Control.AutoSize%2A> indique à un contrôle d'ajuster automatiquement sa taille à son contenu.  Il ne se redimensionnera pas pour être plus petit que la valeur de sa propriété <xref:System.Windows.Forms.Control.Size%2A> d'origine, et il représentera la valeur de sa propriété <xref:System.Windows.Forms.Control.Padding%2A>.  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Création d'un projet Windows Forms  
  
-   Définition des marges de vos contrôles  
  
-   Définition du remplissage de vos contrôles  
  
-   Dimensionnement automatique de vos contrôles  
  
 Lorsque vous aurez terminé, vous aurez assimilé le fonctionnement du rôle joué par ces importantes fonctionnalités de disposition.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Avoir des autorisations suffisantes pour être en mesure de créer et d'exécuter des projets d'application Windows Forms sur l'ordinateur où Visual Studio est installé.  
  
## Création du projet  
 La première étape consiste à créer le projet et configurer le formulaire.  
  
#### Pour créer le projet  
  
1.  Créez un projet d'**application Windows** appelé `LayoutExample`.  Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Sélectionnez le formulaire dans le **Concepteur Windows Forms**.  
  
## Définition des marges de vos contrôles  
 Vous pouvez définir la distance par défaut entre vos contrôles à l'aide de la propriété <xref:System.Windows.Forms.Control.Margin%2A>.  Lorsque vous déplacez un contrôle et le positionnez à proximité d'un autre contrôle, vous voyez une ligne d'alignement \(snapline\) qui affiche les marges des deux contrôles.  Le contrôle que vous déplacez s'alignera également sur la distance définie par les marges.  
  
#### Pour réorganiser les contrôles de votre formulaire à l'aide de la propriété Margin  
  
1.  Faites glisser deux contrôles <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers votre formulaire.  
  
2.  Sélectionnez l'un des contrôles <xref:System.Windows.Forms.Button> et déplacez\-le à proximité de l'autre, jusqu'à ce qu'ils se touchent presque.  
  
     Observez la ligne d'alignement \(snapline\) qui apparaît entre eux.  Cette distance est la somme des valeurs des deux contrôles <xref:System.Windows.Forms.Control.Margin%2A>.  Le contrôle vous déplacez s'aligne sur cette distance.  Pour plus d'informations, consultez [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement \(SnapLines\)](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
3.  Modifiez la propriété <xref:System.Windows.Forms.Control.Margin%2A> de l'un des contrôles en développant l'entrée <xref:System.Windows.Forms.Control.Margin%2A> dans la fenêtre **Propriétés** et en attribuant à la propriété <xref:System.Windows.Forms.Padding.All%2A> la valeur 20.  
  
4.  Sélectionnez l'un des contrôles <xref:System.Windows.Forms.Button> et déplacez\-le près de l'autre.  
  
     La ligne d'alignement \(Snapline\) qui définit la somme des valeurs de marge est plus longue et le contrôle s'aligne sur une distance supérieure par rapport à l'autre contrôle.  
  
5.  Modifiez la propriété <xref:System.Windows.Forms.Control.Margin%2A> du contrôle sélectionné en développant l'entrée <xref:System.Windows.Forms.Control.Margin%2A> dans la fenêtre **Propriétés** et en attribuant à la propriété <xref:System.Windows.Forms.Padding.Top%2A> la valeur 5.  
  
6.  Déplacez le contrôle sélectionné au\-dessous de l'autre contrôle et notez que la ligne d'alignement \(snapline\) est plus courte.  Déplacez le contrôle sélectionné à gauche de l'autre contrôle et notez que la ligne d'ajustement \(SnapLine\) conserve la valeur observée à l'étape 4.  
  
7.  Vous pouvez affecter à chacun des aspects de la propriété <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, des valeurs différentes, ou vous pouvez les affecter tous la même valeur avec la propriété <xref:System.Windows.Forms.Padding.All%2A>.  
  
## Définition du remplissage de vos contrôles  
 Pour réaliser la disposition précise requise pour votre application, vos contrôles contiendront souvent des contrôles enfants.  Lorsque vous souhaitez spécifier la proximité de la bordure du contrôle enfant à la bordure du contrôle parent, utilisez la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle parent conjointement à la propriété <xref:System.Windows.Forms.Control.Margin%2A> du contrôle enfant.  La propriété <xref:System.Windows.Forms.Control.Padding%2A> est également utilisée pour contrôler la proximité du contenu d'un contrôle \(par exemple, la propriété <xref:System.Windows.Forms.Control.Text%2A> d'un contrôle <xref:System.Windows.Forms.Button>\) à ses bordures.  
  
#### Pour réorganiser des contrôles sur votre formulaire à l'aide du remplissage  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers votre formulaire.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur `true`.  
  
3.  Modifiez la propriété <xref:System.Windows.Forms.Control.Padding%2A> en développant l'entrée <xref:System.Windows.Forms.Control.Padding%2A> dans la fenêtre **Propriétés** et en attribuant à la propriété <xref:System.Windows.Forms.Padding.All%2A> la valeur 5.  
  
     Le contrôle se développe pour laisser de la place au nouveau remplissage.  
  
4.  Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> de la **Boîte à outils** vers votre formulaire.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** jusqu'au contrôle <xref:System.Windows.Forms.GroupBox>.  Positionnez le contrôle <xref:System.Windows.Forms.Button> afin qu'il soit affleurant avec le coin inférieur droit du contrôle <xref:System.Windows.Forms.GroupBox>.  
  
     Observez les lignes d'alignement \(snaplines\) qui apparaissent lorsque le contrôle <xref:System.Windows.Forms.Button> s'approche des bordures droite et inférieure du contrôle <xref:System.Windows.Forms.GroupBox>.  Ces lignes d'alignement \(snaplines\) correspondent à la propriété <xref:System.Windows.Forms.Control.Margin%2A> du <xref:System.Windows.Forms.Button>.  
  
5.  Modifiez la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle <xref:System.Windows.Forms.GroupBox> en développant l'entrée <xref:System.Windows.Forms.Control.Padding%2A> dans la fenêtre **Propriétés** et en attribuant à la propriété <xref:System.Windows.Forms.Padding.All%2A> la valeur 20.  
  
6.  Sélectionnez le contrôle <xref:System.Windows.Forms.Button> dans le contrôle <xref:System.Windows.Forms.GroupBox> et déplacez\-le vers le centre du <xref:System.Windows.Forms.GroupBox>.  
  
     Les lignes d'alignement \(snaplines\) apparaissent à une distance supérieure des bordures du contrôle <xref:System.Windows.Forms.GroupBox>.  Cette distance est la somme de la propriété <xref:System.Windows.Forms.Control.Margin%2A> du contrôle <xref:System.Windows.Forms.Button> et de la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle <xref:System.Windows.Forms.GroupBox>.  
  
## Dimensionnement automatique de vos contrôles  
 Dans certaines applications, la taille d'un contrôle ne sera pas la même au moment de l'exécution qu'au moment du design.  Le texte d'un contrôle <xref:System.Windows.Forms.Button>, par exemple, peut être pris dans une base de données et sa longueur ne sera pas connue d'avance.  
  
 Lorsque la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> a la valeur `true`, le contrôle ajuste sa taille à son contenu.  Pour plus d'informations, consultez [Vue d'ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
#### Pour réorganiser les contrôles de votre formulaire à l'aide de la propriété AutoSize  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers votre formulaire.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur `true`.  
  
3.  Modifiez la propriété <xref:System.Windows.Forms.Control.Text%2A> du contrôle <xref:System.Windows.Forms.Button> en lui attribuant la valeur « Ce bouton a une longue chaîne pour sa propriété Text ».  
  
     Lorsque vous validez la modification, le contrôle <xref:System.Windows.Forms.Button> se redimensionne pour contenir le nouveau texte.  
  
4.  Faites glisser un autre contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers votre formulaire.  
  
5.  Modifiez la propriété <xref:System.Windows.Forms.Control.Text%2A> du contrôle <xref:System.Windows.Forms.Button> en lui attribuant la valeur « Ce bouton a une longue chaîne pour sa propriété Text ».  
  
     Lorsque vous validez la modification, le contrôle <xref:System.Windows.Forms.Button> ne se redimensionne pas, et le texte est découpé par le bord droit du contrôle.  
  
6.  Modifiez la propriété <xref:System.Windows.Forms.Control.Padding%2A> en développant l'entrée <xref:System.Windows.Forms.Control.Padding%2A> dans la fenêtre **Propriétés** et en attribuant à la propriété <xref:System.Windows.Forms.Padding.All%2A> la valeur 5.  
  
     Le texte à l'intérieur du contrôle est découpé sur les quatre côtés.  
  
7.  Affectez à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur `true`.  
  
     Le contrôle <xref:System.Windows.Forms.Button> se redimensionne pour contenir la chaîne entière.  Du remplissage a également été ajouté autour du texte, amenant ainsi le contrôle <xref:System.Windows.Forms.Button> à se développer dans les quatre directions.  
  
8.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers votre formulaire.  Positionnez\-le à proximité du coin inférieur droit du formulaire.  
  
9. Affectez à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur `true`.  
  
10. Affectez à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button> les valeurs <xref:System.Windows.Forms.AnchorStyles>, <xref:System.Windows.Forms.AnchorStyles>.  
  
11. Modifiez la propriété <xref:System.Windows.Forms.Control.Text%2A> du contrôle <xref:System.Windows.Forms.Button> en lui attribuant la valeur « Ce bouton a une longue chaîne pour sa propriété Text ».  
  
     Lorsque vous validez la modification, le contrôle <xref:System.Windows.Forms.Button> se redimensionne vers la gauche.  En général, le dimensionnement automatique augmente la taille d'un contrôle dans la direction contraire du paramètre de sa propriété <xref:System.Windows.Forms.Control.Anchor%2A>.  
  
## Propriétés AutoSize et AutoSizeMode  
 Certains contrôles prennent en charge la propriété `AutoSizeMode`, qui vous permet un contrôle plus fin sur le comportement de dimensionnement automatique d'un contrôle.  
  
#### Pour utiliser la propriété AutoSizeMode  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.Panel> de la **Boîte à outils** vers votre formulaire.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Panel> la valeur `true`.  
  
3.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** jusqu'au contrôle <xref:System.Windows.Forms.Panel>.  
  
4.  Placez le contrôle <xref:System.Windows.Forms.Button> près du coin inférieur droit du contrôle <xref:System.Windows.Forms.Panel>.  
  
5.  Sélectionnez le contrôle <xref:System.Windows.Forms.Panel> et saisissez la poignée de redimensionnement inférieure droite.  Redimensionnez le contrôle <xref:System.Windows.Forms.Panel> pour qu'il soit plus grand et plus petit.  
  
    > [!NOTE]
    >  Vous pouvez redimensionner librement le contrôle <xref:System.Windows.Forms.Panel>, mais vous ne pouvez pas le rendre plus petit que la position du coin inférieur droit du contrôle <xref:System.Windows.Forms.Button>.  Ce comportement est spécifié par la valeur par défaut de la propriété `AutoSizeMode`, qui est <xref:System.Windows.Forms.AutoSizeMode>.  
  
6.  Affectez à la propriété `AutoSizeMode` du contrôle <xref:System.Windows.Forms.Panel> la valeur <xref:System.Windows.Forms.AutoSizeMode>.  
  
     Le contrôle <xref:System.Windows.Forms.Panel> se redimensionne autour du contrôle <xref:System.Windows.Forms.Button>.  Vous ne pouvez pas redimensionner le contrôle <xref:System.Windows.Forms.Panel>.  
  
7.  Faites glisser le contrôle <xref:System.Windows.Forms.Button> vers l'angle supérieur gauche du contrôle <xref:System.Windows.Forms.Panel>.  
  
     Le contrôle <xref:System.Windows.Forms.Panel> se redimensionne selon la nouvelle position du contrôle <xref:System.Windows.Forms.Button>.  
  
## Étapes suivantes  
 Il existe de nombreuses autres fonctions de disposition pour réorganiser les contrôles dans vos applications Windows Forms.  Voici quelques combinaisons que vous pouvez essayer :  
  
-   Générez un formulaire à l'aide d'un contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  Pour plus d'informations, consultez [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  Essayez de modifier les valeurs de la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle <xref:System.Windows.Forms.TableLayoutPanel>, ainsi que la propriété <xref:System.Windows.Forms.Control.Margin%2A> sur ses contrôles enfants.  
  
-   Effectuez la même expérience à l'aide d'un contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.  Pour plus d'informations, consultez [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
-   Essayez d'ancrer des contrôles enfants dans un contrôle <xref:System.Windows.Forms.Panel>.  La propriété <xref:System.Windows.Forms.Control.Padding%2A> est une réalisation plus générale de la propriété <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>, et vous pouvez vous vérifier que c'est le cas en mettant un contrôle enfant dans un contrôle <xref:System.Windows.Forms.Panel> et en attribuant à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle enfant la valeur <xref:System.Windows.Forms.DockStyle>.  Attribuez à la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle <xref:System.Windows.Forms.Panel> différentes valeurs et notez l'effet obtenu.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.AutoSize%2A>   
 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>   
 <xref:System.Windows.Forms.Control.Margin%2A>   
 <xref:System.Windows.Forms.Control.Padding%2A>   
 [Vue d'ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement \(SnapLines\)](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)