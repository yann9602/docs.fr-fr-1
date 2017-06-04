---
title: "Comment&#160;: exposer les propri&#233;t&#233;s des contr&#244;les constitutifs | Microsoft Docs"
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
  - "contrôles constitutifs"
  - "contrôles (Windows Forms), constitutifs"
  - "contrôles personnalisés (Windows Forms), exposer des propriétés"
  - "contrôles utilisateur (Windows Forms), exposer les contrôles constitutifs"
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: exposer les propri&#233;t&#233;s des contr&#244;les constitutifs
Les contrôles qui composent un contrôle composite sont appelés *contrôles constitutifs*.  Ces contrôles sont normalement déclarés privés, si bien qu'ils ne sont pas accessibles par le développeur.  Pour mettre à la disposition des futurs utilisateurs certaines propriétés de ces contrôles, vous devez les exposer à l'utilisateur.  Pour exposer une propriété de contrôle constitutif, créez une propriété dans le contrôle utilisateur et utilisez ses accesseurs `get` et `set` pour répercuter la modification dans la propriété privée du contrôle constitutif.  
  
 Prenons l'exemple d'un contrôle utilisateur hypothétique doté d'un bouton constitutif appelé `MyButton`.  Dans cet exemple, lorsque l'utilisateur demande la propriété `ConstituentButtonBackColor`, la valeur enregistrée dans la propriété <xref:System.Windows.Forms.Control.BackColor%2A> de `MyButton` est retournée.  Lorsque l'utilisateur assigne une valeur à cette propriété, cette valeur est automatiquement passée à la propriété <xref:System.Windows.Forms.Control.BackColor%2A> de `MyButton`, après quoi le code `set` s'exécute et modifie la couleur de `MyButton`.  
  
 L'exemple suivant montre comment exposer la propriété <xref:System.Windows.Forms.Control.BackColor%2A> du bouton constitutif :  
  
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
  
### Pour exposer une propriété d'un contrôle constitutif  
  
1.  Créez une propriété publique pour votre contrôle utilisateur.  
  
2.  Dans la section `get` de la propriété, écrivez un code qui récupère la valeur de la propriété à exposer.  
  
3.  Dans la section `set` de la propriété, écrivez du code pour passer la valeur de la propriété à la propriété exposée du contrôle constitutif.  
  
## Voir aussi  
 <xref:System.Windows.Forms.UserControl>   
 [Propriétés dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)   
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)