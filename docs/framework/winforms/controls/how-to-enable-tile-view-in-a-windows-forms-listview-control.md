---
title: "Comment : activer l'affichage en mosaïque dans un contrôle ListView Windows Forms"
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
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad4680490e95da91e72b3b8d6d5f65eec2d115f8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Comment : activer l'affichage en mosaïque dans un contrôle ListView Windows Forms
Avec la fonctionnalité d'affichage en mosaïque du contrôle <xref:System.Windows.Forms.ListView>, vous pouvez fournir un équilibre visuel entre les informations graphiques et textuelles. Les informations textuelles affichées pour un élément dans l'affichage en mosaïque sont identiques aux informations de colonne définies pour le mode Détails. L'affichage en mosaïque fonctionne en association avec les fonctionnalités de regroupement ou de marques d'insertion du contrôle <xref:System.Windows.Forms.ListView>.  
  
 L'affichage en mosaïque utilise une icône de 32 x 32 pixels et plusieurs lignes de texte, comme illustré dans les images suivantes.  
  
 ![Affichage en mosaïque dans un contrôle ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
Texte et icônes de l'affichage en mosaïque  
  
 Pour activer l'affichage en mosaïque, affectez la valeur <xref:System.Windows.Forms.View.Tile> à la propriété <xref:System.Windows.Forms.ListView.View%2A>. Vous pouvez ajuster la taille des mosaïques en définissant la propriété <xref:System.Windows.Forms.ListView.TileSize%2A> et le nombre de lignes de texte affichées dans la mosaïque en ajustant la collection <xref:System.Windows.Forms.ListView.Columns%2A>.  
  
> [!NOTE]
>  L'affichage en mosaïque est disponible uniquement sur [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quand votre application appelle la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Sur les systèmes d'exploitation antérieurs, tout code lié à l'affichage en mosaïque n'a aucun effet et le contrôle <xref:System.Windows.Forms.ListView> s'affiche en mode Grandes icônes. Pour plus d'informations, consultez <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
  
### <a name="to-set-tile-view-programmatically"></a>Pour définir l'affichage en mosaïque par programmation  
  
1.  Utilisez l'énumération <xref:System.Windows.Forms.View> du contrôle <xref:System.Windows.Forms.ListView>.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Exemple  
 L'exemple de code complet suivant illustre l'affichage en mosaïque avec des mosaïques modifiées pour afficher trois lignes de texte. La taille des mosaïques a été ajustée pour empêcher le retour à la ligne.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux assemblys System et System.Windows.Forms.  
  
-   un fichier d'icône nommé book.ico dans le même répertoire que le fichier exécutable.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également la page [Comment : compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [Contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Vue d’ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Fonctionnalités de Windows XP et contrôles Windows Forms](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
