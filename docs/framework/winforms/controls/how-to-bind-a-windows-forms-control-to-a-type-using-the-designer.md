---
title: "Comment&#160;: lier un contr&#244;le Windows Forms &#224; un type &#224; l&#39;aide du concepteur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "BindingSource (composant Windows Forms), liaison à un type"
  - "contrôles (Windows Forms), liaison à un type"
  - "types (Windows Forms), lier des contrôles à"
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: lier un contr&#244;le Windows Forms &#224; un type &#224; l&#39;aide du concepteur
Lorsque vous générez des contrôles qui interagissent avec les données, il vous faut parfois lier un contrôle à un type, plutôt qu'à un objet.  Vous devez généralement lier un contrôle à un type au moment du design, lorsque les données ne sont pas toujours disponibles, mais souhaitez tout de même que vos contrôles liés aux données affichent des données provenant de l'interface publique d'un type.  Les procédures suivantes montrent comment créer une nouvelle <xref:System.Windows.Forms.BindingSource> qui est liée à un type, puis comment lier une des propriétés du type à la propriété <xref:System.Windows.Forms.TextBox.Text%2A> d'une <xref:System.Windows.Forms.TextBox>.  
  
### Pour lier la source de liaison à un type  
  
1.  Créez un projet Windows Forms.  
  
     Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  En mode **Design**, faites glisser un composant <xref:System.Windows.Forms.BindingSource> sur le formulaire.  
  
3.  Dans la fenêtre **Propriétés**, cliquez sur la flèche en regard de la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A>.  
  
4.  Dans l'**Éditeur de types muni d'une interface utilisateur DataSource**, cliquez sur **Ajouter la source de données du projet**.  
  
5.  Dans la page **Choisir un type de source de données**, sélectionnez **Objet**, puis cliquez sur **Suivant**.  
  
6.  Sélectionnez le type auquel vous lier :  
  
    -   Si le type auquel vous voulez vous lier se trouve dans le projet actuel, ou l'assembly qui contient le type est déjà ajouté comme une référence, développez les nœuds pour rechercher le type vous voulez, puis sélectionnez\-le.  
  
         ou  
  
    -   Si le type auquel vous souhaitez vous lier se trouve dans un autre assembly, ne figurant pas actuellement dans la liste de références, cliquez sur **Ajouter une référence**, puis cliquez sur l'onglet **Projets**.  Sélectionnez le projet qui contient l'objet métier voulu, puis cliquez sur **OK**.  Ce projet apparaîtra dans la liste d'assemblys, ce qui vous permettra de développer les nœuds pour rechercher et sélectionner le type que vous voulez.  
  
        > [!NOTE]
        >  Si vous souhaitez créer une liaison avec un type dans une infrastructure ou un assembly Microsoft, désactivez la case à cocher **Masquer les assemblys qui commencent par Microsoft ou System**.  
  
7.  Cliquez sur **Suivant**, puis sur **Terminer**.  
  
### Pour lier le contrôle à la source de liaison  
  
1.  Ajoutez <xref:System.Windows.Forms.TextBox> au formulaire.  
  
2.  Dans la fenêtre **Propriétés**, développez le nœud **\(DataBindings\)**.  
  
3.  Cliquez sur la flèche en regard de la propriété <xref:System.Windows.Forms.TextBox.Text%2A>.  
  
4.  Dans l'**Éditeur de types muni d'une interface utilisateur DataSource**, développez le nœud de la <xref:System.Windows.Forms.BindingSource> précédemment ajoutée et sélectionnez la propriété du type dépendant que vous souhaitez lier à la propriété <xref:System.Windows.Forms.TextBox.Text%2A> de la <xref:System.Windows.Forms.TextBox>.  
  
## Voir aussi  
 [Composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [Comment : lier un contrôle Windows Forms à un type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)   
 [Liaison de contrôles à des données dans Visual Studio](../Topic/Bind%20controls%20to%20data%20in%20Visual%20Studio.md)