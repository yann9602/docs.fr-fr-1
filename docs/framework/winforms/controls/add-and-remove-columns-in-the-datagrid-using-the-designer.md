---
title: "Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b314fe58413c0a284f5ebb41642e8c8dd1fb02b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur
Windows Forms <xref:System.Windows.Forms.DataGridView> contrôle doit contenir des colonnes pour afficher des données. Si vous envisagez de remplir le contrôle manuellement, vous devez ajouter les colonnes vous-même. Ou bien, vous pouvez lier le contrôle à une source de données, ce qui génère et remplit automatiquement les colonnes. Si la source de données contient plus de colonnes que vous souhaitez afficher, vous pouvez supprimer les colonnes inutiles.  
  
 Les procédures suivantes requièrent une **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.DataGridView> contrôle. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-column-using-the-designer"></a>Pour ajouter une colonne à l’aide du Concepteur  
  
1.  Cliquez sur le glyphe de balise active (![glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le coin supérieur droit de la <xref:System.Windows.Forms.DataGridView> contrôler, puis sélectionnez **ajouter une colonne**.  
  
2.  Dans le **ajouter une colonne** boîte de dialogue, choisissez le **colonne liée aux données** option et sélectionnez une colonne de la source de données ou choisissez la **colonne indépendante** option et définissez la colonne à l’aide des champs fournis.  
  
3.  Cliquez sur le **ajouter** pour ajouter la colonne, qui n’apparaissent dans le concepteur si les colonnes existantes ne remplissent pas déjà de la zone d’affichage de contrôle.  
  
    > [!NOTE]
    >  Vous pouvez modifier les propriétés des colonnes dans le **modifier les colonnes** la boîte de dialogue, vous pouvez accéder à partir de la balise du contrôle.  
  
### <a name="to-remove-a-column-using-the-designer"></a>Pour supprimer une colonne à l’aide du Concepteur  
  
1.  Choisissez **modifier les colonnes** à partir de la balise du contrôle.  
  
2.  Sélectionnez une colonne dans la **colonnes sélectionnées** liste.  
  
3.  Cliquez sur le **supprimer** bouton pour supprimer la colonne, qui n’apparaît plus dans le concepteur.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
