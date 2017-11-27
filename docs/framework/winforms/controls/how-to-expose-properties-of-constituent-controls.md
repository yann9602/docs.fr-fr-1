---
title: "Comment : exposer les propriétés des contrôles constitutifs"
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
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb85cb77c28ad443fb6837a5305a080c450220f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Comment : exposer les propriétés des contrôles constitutifs
Les contrôles qui composent un contrôle composite sont appelés *contrôles constitutifs*. Ces contrôles sont normalement déclarés privés et donc ne peut pas être accessible par le développeur. Si vous souhaitez rendre les propriétés de ces contrôles accessibles aux utilisateurs de futures, vous devez les exposer à l’utilisateur. Une propriété d’un contrôle qui le composent est exposée par la création d’une propriété dans le contrôle utilisateur et à l’aide de la `get` et `set` accesseurs pour répercuter la modification dans la propriété privée du contrôle constitutif.  
  
 Considérez un contrôle utilisateur hypothétique avec un bouton constitutif appelé `MyButton`. Dans cet exemple, lorsque l’utilisateur demande la `ConstituentButtonBackColor` propriété, la valeur stockée dans le <xref:System.Windows.Forms.Control.BackColor%2A> propriété du `MyButton` est remis. Lorsque l’utilisateur assigne une valeur à cette propriété, cette valeur est automatiquement passée à la <xref:System.Windows.Forms.Control.BackColor%2A> propriété du `MyButton` et `set` code s’exécutera, changez la couleur du `MyButton`.  
  
 L’exemple suivant montre comment exposer le <xref:System.Windows.Forms.Control.BackColor%2A> propriété du bouton constitutif :  
  
```vb  
Public Property ButtonColor() as System.Drawing.Color  
   Get  
      Return MyButton.BackColor  
   End Get  
   Set(Value as System.Drawing.Color)  
      MyButton.BackColor = Value  
   End Set  
End Property  
```  
  
```csharp  
public Color ButtonColor  
{  
   get  
   {  
      return(myButton.BackColor);  
   }  
   set  
   {  
      myButton.BackColor = value;  
   }  
}  
```  
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>Pour exposer une propriété d’un contrôle qui le composent  
  
1.  Créez une propriété publique pour votre contrôle utilisateur.  
  
2.  Dans la `get` section de la propriété, écrire du code qui Récupère la valeur de la propriété que vous souhaitez exposer.  
  
3.  Dans la `set` section de la propriété, écrire du code qui transmet la valeur de la propriété à la propriété exposée du contrôle constitutif.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.UserControl>  
 [Propriétés dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
