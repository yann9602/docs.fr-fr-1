---
title: "Comment : afficher des données liées dans un contrôle DataRepeater (Visual Studio) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9bf8f2f5fcc4dfa2b29e368a4e26bf112e08149e
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>Comment : afficher des données liées dans un contrôle DataRepeater (Visual Studio)
L’utilisation la plus courante de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle consiste à afficher des données liées à partir d’une base de données ou autre source de données.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 En plus des contrôles dépendants, vous pouvez souhaiter ajouter d’autres contrôles, par exemple une étiquette statique ou une image répétée sur chaque élément de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Pour plus d’informations, consultez [Comment : afficher des contrôles indépendants dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
 Vous pouvez également lier à une source de données au moment de l’exécution en définissant le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>propriété `True` et en assignant une source de données pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A>propriété.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> Dans ce cas, vous devrez gérer l’interaction avec la source de données. Pour plus d’informations, consultez [Mode virtuel dans le contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>Pour créer un DataRepeater lié aux données  
  
1.  Faites glisser un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôler à partir de la **Visual Basic PowerPacks** onglet le **boîte à outils** à un formulaire ou un contrôle conteneur.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Faites glisser les poignées de dimensionnement et de déplacement pour redimensionner et positionner le contrôle.  
  
     Notez que le contrôle possède deux régions rectangulaires. La région supérieure est la *modèle d’élément*; les contrôles ajoutés au modèle seront répétés dans chaque élément dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle au moment de l’exécution.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> La région inférieure est la *viewport*, où les éléments seront affiche.  
  
     Vous pouvez également redimensionner et positionner le contrôle ou le modèle d’élément en modifiant le **taille** et **Position** propriétés dans la fenêtre Propriétés.  
  
3.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.  
  
    > [!NOTE]
    >  Si le **des Sources de données** fenêtre est vide, ajoutez une source de données à celle-ci. Pour plus d’informations, consultez [ajouter de nouvelles sources de données](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).  
  
4.  Dans le **des Sources de données** fenêtre, sélectionnez le nœud de niveau supérieur pour la table qui contient les données que vous souhaitez lier.  
  
5.  Modifier le type de déplacement de la table à `Details` en cliquant sur `Details` dans la liste déroulante du nœud table.  
  
6.  Sélectionnez le nœud table et faites-le glisser sur la région de modèle d’élément de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
     Vous pouvez spécifier des types de contrôles sont affichés pour chaque champ. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](https://docs.microsoft.com/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Comment : afficher les contrôles indépendants dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [Comment : créer un formulaire maître/détail en utilisant deux contrôles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [Comment : modifier l’apparence d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Dépannage des problèmes liés au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
