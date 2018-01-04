---
title: "Comment : naviguer au sein des données dans les Windows Forms"
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
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d99d794164307cb22c5dfc89d6c9c227aa457a59
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Comment : naviguer au sein des données dans les Windows Forms
Dans une application Windows, pour parcourir les enregistrements dans une source de données le plus simple consiste à lier un <xref:System.Windows.Forms.BindingSource> à la source de données, puis lier les contrôles à le <xref:System.Windows.Forms.BindingSource>. Vous pouvez ensuite utiliser la méthode de navigation intégrée sur le <xref:System.Windows.Forms.BindingSource> telle une <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> et <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. À l’aide de ces méthodes s’ajuste le <xref:System.Windows.Forms.BindingSource.Position%2A> et <xref:System.Windows.Forms.BindingSource.Current%2A> propriétés de la <xref:System.Windows.Forms.BindingSource> en conséquence. Vous pouvez également rechercher un élément et définissez-le en tant que l’élément actuel en définissant le <xref:System.Windows.Forms.BindingSource.Position%2A> propriété.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Pour incrémenter la position dans une source de données  
  
1.  Définir le <xref:System.Windows.Forms.BindingSource.Position%2A> propriété de la <xref:System.Windows.Forms.BindingSource> de vos données liées à la position de l’enregistrement à atteindre. L’exemple suivant illustre l’utilisation de la <xref:System.Windows.Forms.BindingSource.MoveNext%2A> méthode de la <xref:System.Windows.Forms.BindingSource> pour incrémenter la <xref:System.Windows.Forms.BindingSource.Position%2A> propriété lorsque le `nextButton` un clic sur. Le <xref:System.Windows.Forms.BindingSource> est associé le `Customers` table d’un dataset `Northwind`.  
  
    > [!NOTE]
    >  Définition de la <xref:System.Windows.Forms.BindingSource.Position%2A> propriété avec une valeur au-delà du premier ou dernier enregistrement n’entraîne pas d’erreur, comme le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] pas vous permettra de définir la position à une valeur en dehors des limites de la liste. S’il est important dans votre application pour savoir si vous avez dépassé le premier ou dernier enregistrement, inclure une logique permettant de tester si vous dépassez le nombre d’éléments de données.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Pour vérifier si vous avez dépassé la fin ou au début  
  
1.  Créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.BindingSource.PositionChanged>. Dans le gestionnaire, vous pouvez tester si la valeur de position proposée a dépassé le nombre d’éléments de données réelles.  
  
     L’exemple suivant illustre comment vous pouvez tester si vous avez atteint le dernier élément de données. Dans l’exemple, si vous êtes sur le dernier élément, le **suivant** bouton sur le formulaire est désactivé.  
  
    > [!NOTE]
    >  Gardez à l’esprit que, vous modifiez la liste vous naviguez dans le code, vous devez réactiver la **suivant** bouton, afin que les utilisateurs peuvent rechercher toute la longueur de la nouvelle liste. En outre, sachez que ci-dessus <xref:System.Windows.Forms.BindingSource.PositionChanged> événement spécifique <xref:System.Windows.Forms.BindingSource> vous travaillez doit être associé à sa méthode de gestion d’événements. Voici un exemple d’une méthode permettant de gérer le <xref:System.Windows.Forms.BindingSource.PositionChanged> événement :  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Pour rechercher un élément et le définir comme élément actuel  
  
1.  Rechercher l’enregistrement que vous souhaitez définir comme élément actuel. Ce faire, vous pouvez utiliser la <xref:System.Windows.Forms.BindingSource.Find%2A> méthode de la <xref:System.Windows.Forms.BindingSource>, si votre source de données implémente <xref:System.ComponentModel.IBindingList>. Quelques exemples de données sources qui implémentent <xref:System.ComponentModel.IBindingList> sont <xref:System.ComponentModel.BindingList%601> et <xref:System.Data.DataView>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données prises en charge par les Windows Forms](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [Notification de modifications dans la liaison de données Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Liaison de données et Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
