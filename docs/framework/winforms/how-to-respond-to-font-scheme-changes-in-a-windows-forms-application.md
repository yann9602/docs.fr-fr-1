---
title: "Comment&#160;: r&#233;pondre aux modifications de jeu de polices dans une application Windows&#160;Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Windows Forms, modifications de jeu de polices"
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: r&#233;pondre aux modifications de jeu de polices dans une application Windows&#160;Forms
Dans les systèmes d'exploitation Windows, un utilisateur peut modifier les paramètres de police à l'échelle du système pour que la police par défaut apparaisse dans une taille plus grande ou plus petite.  La modification de ces paramètres de police est critique pour les utilisateurs souffrant d'une faible acuité visuelle et qui nécessitent la présence d'un texte en gros caractères sur leurs écrans.  Vous pouvez ajuster votre application Windows Forms de façon à tenir compte de ces modifications en augmentant ou en diminuant la taille du formulaire et de tout le contenu du texte chaque fois que le jeu de polices change.  Si vous souhaitez que votre formulaire s'adapte dynamiquement aux modifications intervenant dans les tailles de polices, vous pouvez ajouter du code à votre formulaire.  
  
 En général, la police par défaut utilisée par les Windows Forms est la police retournée par l'appel de l'espace de noms <xref:Microsoft.Win32> à `GetStockObject(DEFAULT_GUI_FONT)`.  La police retournée par cet appel change uniquement lorsque la résolution d'écran change.  Comme indiqué dans la procédure suivante, votre code doit remplacer la police par défaut par <xref:System.Drawing.SystemFonts.IconTitleFont%2A> afin de tenir compte des modifications dans la taille de police.  
  
### Pour utiliser la police de bureau et répondre aux modifications de jeu de polices  
  
1.  Créez votre formulaire et ajoutez\-lui les contrôles de votre choix.  Pour plus d'informations, consultez [Comment : créer une application Windows Forms à partir de la ligne de commande](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) et [Contrôles à utiliser dans les Windows Forms](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).  
  
2.  Ajoutez une référence à l'espace de noms <xref:Microsoft.Win32> de votre code.  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  Ajoutez le code suivant au constructeur de votre formulaire pour effectuer le raccordement des gestionnaires d'événements requis, et modifier la police par défaut utilisée pour le formulaire.  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  Implémentez un gestionnaire pour l'événement <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> qui fait que le formulaire s'adapte automatiquement lors du changement de la catégorie <xref:Microsoft.Win32.UserPreferenceCategory>.  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  Enfin, implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.Form.FormClosing> qui détache le gestionnaire d'événements <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.  
  
> [!IMPORTANT]
>  Si ce code n'est pas inclus, votre application connaîtra une fuite de mémoire.  
  
 [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
 [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
1.  Compilez et exécutez le code.  
  
### Pour modifier manuellement le jeu de polices dans Windows XP  
  
1.  Pendant que votre application Windows Forms s'exécute, cliquez avec le bouton droit sur le bureau de Windows et choisissez **Propriétés** dans le menu contextuel.  
  
2.  Dans la boîte de dialogue **Propriétés d'affichage**, cliquez sur l'onglet **Apparence**.  
  
3.  De la zone de liste déroulante **Taille de police**, sélectionnez une nouvelle taille de police.  
  
     Vous remarquerez que le formulaire réagit maintenant aux modifications effectuées au moment de l'exécution dans le jeu de polices de bureau.  Lorsque l'utilisateur bascule entre **Normal**, **Grandes polices** et **Très grands caractères**, le formulaire modifie correctement polices et échelles.  
  
## Exemple  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 Dans cet exemple de code, le constructeur contient un appel à `InitializeComponent`, qui est défini lorsque vous créez un nouveau projet Windows Forms dans Visual Studio.  Supprimez cette ligne de code si vous générez votre application à partir de la ligne de commande.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>   
 [Mise à l'échelle automatique dans les Windows Forms](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)