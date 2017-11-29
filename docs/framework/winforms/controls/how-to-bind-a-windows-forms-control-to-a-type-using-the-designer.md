---
title: "Comment : lier un contrôle Windows Forms à un type à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 215a69a47b0588e45fcc28202dce4c6210b1dfe6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Comment : lier un contrôle Windows Forms à un type à l'aide du concepteur
Quand vous créez des contrôles qui interagissent avec des données, vous devez parfois lier un contrôle à un type plutôt qu’à un objet. Cette situation se présente surtout au moment du design, quand les données peuvent ne pas être disponibles mais que vos contrôles liés aux données ont tout de même besoin d’afficher des informations à partir de l’interface publique d’un type. Les procédures suivantes montrent comment créer un nouveau <xref:System.Windows.Forms.BindingSource> qui est liée à un type, puis comment lier une des propriétés du type pour le <xref:System.Windows.Forms.TextBox.Text%2A> propriété d’un <xref:System.Windows.Forms.TextBox>.  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a>Pour lier le BindingSource à un type  
  
1.  Créez un projet Windows Forms.  
  
     Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Dans **conception** afficher, faites glisser un <xref:System.Windows.Forms.BindingSource> composant vers le formulaire.  
  
3.  Dans le **propriétés** fenêtre, cliquez sur la flèche pour la <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriété.  
  
4.  Dans l’**éditeur de types d’interface utilisateur DataSource**, cliquez sur **Ajouter la source de données du projet**.  
  
5.  Sur la page **Choisir un type de source de données**, sélectionnez **Objet**, puis cliquez sur **Suivant**.  
  
6.  Sélectionnez le type à lier :  
  
    -   Si le type avec lequel vous souhaitez établir une liaison se trouve dans le projet actuel, ou si l’assembly qui contient ce type est déjà ajouté en tant que référence, développez les nœuds pour rechercher le type souhaité et sélectionnez-le.  
  
         ou  
  
    -   Si le type avec lequel vous souhaitez établir une liaison se trouve actuellement dans un autre assembly, et non dans la liste de références, cliquez sur **Ajouter une référence**, puis cliquez sur l’onglet **Projets**. Sélectionnez le projet contenant l’objet métier de votre choix, puis cliquez sur **OK**. Ce projet apparaît dans la liste des assemblys. Vous pouvez donc développer les nœuds pour rechercher le type que vous souhaitez, puis le sélectionner.  
  
        > [!NOTE]
        >  Pour effectuer une liaison avec un type présent dans une infrastructure ou un assembly Microsoft, décochez la case **Masquer les assemblys qui commencent par Microsoft ou System**.  
  
7.  Cliquez sur **Suivant**, puis sur **Terminer**.  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a>Pour lier le contrôle au BindingSource  
  
1.  Ajoutez un <xref:System.Windows.Forms.TextBox> au formulaire.  
  
2.  Dans la fenêtre **Propriétés**, développez le nœud **(DataBindings)**.  
  
3.  Cliquez sur la flèche en regard du <xref:System.Windows.Forms.TextBox.Text%2A> propriété.  
  
4.  Dans le **éditeur de Type de source de données de l’interface utilisateur**, développez le nœud pour le <xref:System.Windows.Forms.BindingSource> précédemment ajoutée et sélectionnez la propriété du type dépendant que vous souhaitez lier à la <xref:System.Windows.Forms.TextBox.Text%2A> propriété de la <xref:System.Windows.Forms.TextBox>.  
  
## <a name="see-also"></a>Voir aussi  
 [BindingSource, composant](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Comment : lier un contrôle Windows Forms à un type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [Lier des contrôles à des données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
