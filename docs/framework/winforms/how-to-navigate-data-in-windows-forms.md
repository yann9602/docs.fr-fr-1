---
title: "Comment&#160;: naviguer au sein des donn&#233;es dans les Windows Forms | Microsoft Docs"
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
  - "CurrencyManager (classe), naviguer dans des données Windows Forms"
  - "curseurs, sources de données"
  - "données (Windows Forms), naviguer"
  - "sources de données, Windows Forms"
  - "Windows Forms, naviguer"
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: naviguer au sein des donn&#233;es dans les Windows Forms
Dans une application Windows, la manière la plus simple de circuler entre les enregistrements dans une source de données est de lier un composant <xref:System.Windows.Forms.BindingSource> à la source de données et puis de lier les contrôles à la <xref:System.Windows.Forms.BindingSource>.  Vous pouvez utiliser ensuite la méthode de navigation intégrée sur la <xref:System.Windows.Forms.BindingSource> telle que <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> et <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.  L'utilisation de ces méthodes règle convenablement les propriétés <xref:System.Windows.Forms.BindingSource.Position%2A> et <xref:System.Windows.Forms.BindingSource.Current%2A> de la <xref:System.Windows.Forms.BindingSource>.  Vous pouvez également rechercher un élément et le définir comme élément actuel en définissant la propriété <xref:System.Windows.Forms.BindingSource.Position%2A>.  
  
### Pour incrémenter la position dans une source de données  
  
1.  Définissez, pour la propriété <xref:System.Windows.Forms.BindingSource.Position%2A> de l'objet <xref:System.Windows.Forms.BindingSource> de vos données liées, la position de l'enregistrement auquel vous voulez accéder.  L'exemple suivant illustre l'utilisation de la méthode <xref:System.Windows.Forms.BindingSource.MoveNext%2A> du <xref:System.Windows.Forms.BindingSource> pour incrémenter la propriété <xref:System.Windows.Forms.BindingSource.Position%2A> lorsque vous cliquez sur `nextButton`.  L'objet <xref:System.Windows.Forms.BindingSource> est associé à la table `Customers` du groupe de données `Northwind`.  
  
    > [!NOTE]
    >  La définition de la propriété <xref:System.Windows.Forms.BindingSource.Position%2A> avec une valeur au\-delà du premier ou du dernier enregistrement ne génère pas d'erreur puisque le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ne vous permet pas de définir, pour la position, une valeur en dehors des limites de la liste.  S'il est important, pour l'application, de savoir si vous avez dépassé le premier ou le dernier enregistrement, incluez une logique pour vérifier si vous dépassez le nombre d'éléments de données.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### Pour vérifier si vous avez dépassé le début ou la fin  
  
1.  Créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.BindingSource.PositionChanged>.  Dans le gestionnaire, vous pouvez vérifier si la valeur de position proposée a effectivement dépassé le nombre d'éléments de données.  
  
     L'exemple suivant montre comment vous pouvez vérifier si vous avez atteint le dernier élément de données.  Dans l'exemple, lorsque vous vous trouvez sur le dernier élément, le bouton **Suivant** est désactivé.  
  
    > [!NOTE]
    >  Si vous modifiez la liste actuellement parcourue dans le code, réactivez le bouton **Suivant** pour que les utilisateurs puissent parcourir la nouvelle liste sur toute sa longueur.  En outre, sachez que l'événement <xref:System.Windows.Forms.BindingSource.PositionChanged> ci\-dessus du <xref:System.Windows.Forms.BindingSource> spécifique avec lequel vous travaillez doit être associé à sa méthode de gestion d'événements.  L'exemple suivant illustre une méthode visant à gérer l'événement <xref:System.Windows.Forms.BindingSource.PositionChanged> :  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### Pour rechercher un élément et le définir comme élément actuel  
  
1.  Recherchez l'enregistrement que vous souhaitez définir comme élément actuel.  Pour ce faire, utilisez la méthode <xref:System.Windows.Forms.BindingSource.Find%2A> de l'objet <xref:System.Windows.Forms.BindingSource>, si votre source de données implémente <xref:System.ComponentModel.IBindingList>.  Quelques exemples de sources de données qui implémentent <xref:System.ComponentModel.IBindingList> sont <xref:System.ComponentModel.BindingList%601> et <xref:System.Data.DataView>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## Voir aussi  
 [Sources de données prises en charge par les Windows Forms](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)   
 [Notification de modifications dans la liaison de données Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)   
 [Liaison de données et Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)