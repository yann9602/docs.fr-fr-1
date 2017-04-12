---
title: "Comment : créer un formulaire maître / détail en utilisant deux contrôles DataRepeater (Visual Studio) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: 7
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 23789bb11cab17b50928651e1dc00d5d59640c0f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>Comment : créer un formulaire maître/détail en utilisant deux contrôles DataRepeater (Visual Studio)
Vous pouvez afficher les données associées à l’aide de deux ou plusieurs <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôles pour créer un formulaire maître/détail.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Par exemple, vous souhaiterez afficher une liste de clients dans une <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>et lorsque l’utilisateur sélectionne un client, afficher la liste des commandes de ce client dans un deuxième <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 Vous pouvez afficher les données associées en faisant glisser des éléments de détail qui partagent le même nœud de la table principale de la **des Sources de données** fenêtre sur un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Par exemple, si vous avez une source de données qui possède une table Customers et une table connexe Orders, vous consultez les deux tables en tant que nœuds de niveau supérieur dans l’arborescence de la **des Sources de données** fenêtre. Développez le nœud clients afin que vous puissiez voir les colonnes. Notez que la dernière colonne de la liste est un nœud extensible qui représente la table Orders. Ce nœud représente les commandes connexes d’un client.  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>Pour afficher les données associées dans deux contrôles DataRepeater  
  
1.  Faites glisser deux <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>des contrôles de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un formulaire ou un contrôle conteneur.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Faites glisser les poignées de dimensionnement et de déplacement pour redimensionner les contrôles et les positionner côte à côte.  
  
3.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.  
  
    > [!NOTE]
    >  Si le **des Sources de données** fenêtre est vide, ajoutez une source de données à celle-ci. Pour plus d’informations, consultez [ajouter de nouvelles sources de données](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).  
  
4.  Dans le **des Sources de données** fenêtre, sélectionnez le nœud de niveau supérieur pour la table principale.  
  
5.  Modifier le type de déplacement de la table principale sur Détails en cliquant sur **détails** dans la liste déroulante du nœud table.  
  
6.  Faites glisser le nœud de la table principale sur la région de modèle d’élément du premier <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
7.  Développez le nœud de la table principale et sélectionnez le nœud secondaire de la table associée.  
  
8.  Modifier le type de déplacement de la table secondaire sur Détails en cliquant sur **détails** dans la liste déroulante du nœud table.  
  
9. Sélectionnez ce nœud table et faites-le glisser sur la région de modèle d’élément de la seconde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Comment : afficher des données liées dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [Comment : afficher liées à des données dans un Windows Forms Application](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)   
 [Comment : modifier l’apparence d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Dépannage des problèmes liés au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
