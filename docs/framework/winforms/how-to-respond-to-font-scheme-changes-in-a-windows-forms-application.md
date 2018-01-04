---
title: "Comment : répondre aux modifications de jeu de polices dans une application Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aac8d56c87ff03b313565a3d04cd3f3cc4e85f72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>Comment : répondre aux modifications de jeu de polices dans une application Windows Forms
Dans les systèmes d’exploitation Windows, un utilisateur peut modifier les paramètres de police de l’échelle du système pour que la police par défaut s’affiche plus ou moins volumineux. La modification de ces paramètres de police est critique pour les utilisateurs malvoyants et requièrent un type plus grand lire le texte à l’écran. Vous pouvez ajuster votre application Windows Forms pour réagir à ces modifications en augmentant ou en réduisant la taille du formulaire et tous ses chaque fois que le jeu de polices change. Si vous souhaitez que votre formulaire pour prendre en compte les modifications dans les tailles de police dynamiquement, vous pouvez ajouter le code à votre formulaire.  
  
 En règle générale, la police par défaut utilisée par les Windows Forms est la police retournée par le <xref:Microsoft.Win32> appel d’espace de noms à `GetStockObject(DEFAULT_GUI_FONT)`. La police retournée par cet appel change uniquement lorsque la résolution d’écran change. Comme indiqué dans la procédure suivante, votre code doit modifier la police par défaut à <xref:System.Drawing.SystemFonts.IconTitleFont%2A> pour répondre aux modifications de taille de police.  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>Pour utiliser la police de bureau et répondre aux modifications de jeu de polices  
  
1.  Créer votre formulaire et les contrôles que vous souhaitez ajouter. Pour plus d’informations, consultez [Comment : créer une Application Windows Forms à partir de la ligne de commande](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) et [contrôles à utiliser dans les Windows Forms](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).  
  
2.  Ajoutez une référence à la <xref:Microsoft.Win32> espace de noms à votre code.  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  Ajoutez le code suivant au constructeur de votre formulaire pour raccorder des gestionnaires d’événements requis et pour modifier la police par défaut en cours d’utilisation pour le formulaire.  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  Implémentez un gestionnaire pour le <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> événement qui provoque le formulaire à l’échelle automatiquement lorsque la <xref:Microsoft.Win32.UserPreferenceCategory.Window> changements de catégorie.  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  Enfin, implémentez un gestionnaire pour le <xref:System.Windows.Forms.Form.FormClosing> événement détache le <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Gestionnaire d’événements.  
  
> [!IMPORTANT]
>  Échec d’inclure ce code met à votre application une fuite de mémoire.  
  
 [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
 [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
1.  Compilez, puis exécutez le code.  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Pour modifier manuellement le jeu de polices dans Windows XP  
  
1.  Pendant l’exécution de votre application Windows Forms, cliquez sur le bureau Windows, puis choisissez **propriétés** dans le menu contextuel.  
  
2.  Dans le **propriétés d’affichage** boîte de dialogue, cliquez sur le **apparence** onglet.  
  
3.  À partir de la **la taille de police** liste déroulante, sélectionnez une nouvelle taille de police.  
  
     Vous remarquerez que le formulaire réagit maintenant pour exécuter ces modifications dans le jeu de polices de bureau. Lorsque l’utilisateur change entre **Normal**, **polices de grande taille**, et **très grands caractères**, le formulaire modifie la police et met à l’échelle correctement.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 Dans cet exemple de code, le constructeur contienne un appel à `InitializeComponent`, qui est défini lorsque vous créez un nouveau projet Windows Forms dans Visual Studio. Supprimez cette ligne de code si vous générez votre application sur la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 [Mise à l'échelle automatique dans les Windows Forms](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)
