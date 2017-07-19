---
title: "Contr&#244;les dessin&#233;s par l&#39;utilisateur | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), dessiné par l'utilisateur"
  - "OnPaint (méthode Windows Forms)"
  - "contrôles dessinés par l'utilisateur (Windows Forms)"
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Contr&#244;les dessin&#233;s par l&#39;utilisateur
Avec le .NET Framework, vous pouvez très facilement développer vos propres contrôles.  Vous pouvez créer un contrôle utilisateur, c'est\-à\-dire des contrôles standard liés ensemble par du code, ou créer votre propre contrôle en partant de zéro.  Vous pouvez même utiliser l'héritage pour créer un contrôle héritant d'un contrôle existant et compléter ses fonctionnalités inhérentes.  Quelle que soit la méthode choisie, le .NET Framework met à votre disposition les fonctionnalités qui vous permettront de dessiner une interface graphique personnalisée pour tout contrôle que vous créerez.  
  
 Pour peindre un contrôle, vous exécutez le code de sa méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.  L'unique argument de la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> est un objet <xref:System.Windows.Forms.PaintEventArgs> qui fournit toutes les informations et toutes les fonctionnalités nécessaires au rendu de votre contrôle.  <xref:System.Windows.Forms.PaintEventArgs> fournit sous forme de propriétés deux objets principaux à utiliser pour le rendu de votre contrôle :  
  
-   Objet <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> : le rectangle qui représente la partie du contrôle qui sera dessinée.  Il peut s'agir du contrôle entier ou d'une partie du contrôle, selon la façon dont celui\-ci est dessiné.  
  
-   Objet <xref:System.Drawing.Graphics> : encapsule plusieurs méthodes et objets graphiques fournissant les fonctionnalités qui vous sont nécessaires pour dessiner le contrôle.  
  
 Pour plus d'informations sur l'objet <xref:System.Drawing.Graphics> et son utilisation, consultez [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 L'événement <xref:System.Windows.Forms.Control.OnPaint%2A> est déclenché chaque fois que le contrôle est dessiné ou actualisé à l'écran, et l'objet <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> représente le rectangle dans lequel le dessin est effectué.  Si le contrôle entier doit être actualisé, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> représente la taille du contrôle entier.  En revanche, si seulement une partie du contrôle doit être actualisée, l'objet <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> représente uniquement la région qui doit être redessinée.  Un tel cas peut, par exemple, se produire lorsqu'un contrôle était partiellement caché par un autre contrôle ou formulaire dans l'interface utilisateur.  
  
 Lorsque vous héritez de la classe <xref:System.Windows.Forms.Control>, vous devez substituer le contenu de la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> par votre propre code de rendu graphique.  Si vous voulez fournir une interface graphique personnalisée à un contrôle utilisateur ou hérité, vous pouvez également le faire en substituant la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.  Voici un exemple :  
  
```vb  
Protected Overrides Sub OnPaint(ByVal pe As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(pe)  
  
   ' Declare and instantiate a drawing pen.  
   Dim myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
  
   ' Draw an aqua rectangle in the rectangle represented by the control.  
   pe.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
End Sub  
  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs pe)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(pe);  
  
   // Declare and instantiate a new pen.  
   System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua);  
  
   // Draw an aqua rectangle in the rectangle represented by the control.  
   pe.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,   
      this.Size));  
}  
  
```  
  
 L'exemple précédent montre comment définir pour un contrôle une représentation graphique très simple.  Il appelle la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de la classe de base, crée un objet <xref:System.Drawing.Pen> utilisé pour dessiner, puis dessine une ellipse dans le rectangle déterminé par les paramètres <xref:System.Windows.Forms.Control.Location%2A> et <xref:System.Windows.Forms.Control.Size%2A> du contrôle.  Même si, en général, le code de rendu est sensiblement plus complexe que celui\-ci, cet exemple montre comment utiliser l'objet <xref:System.Drawing.Graphics> contenu dans l'objet <xref:System.Windows.Forms.PaintEventArgs>.  Notez que si vous héritez d'une classe telle que <xref:System.Windows.Forms.UserControl> ou <xref:System.Windows.Forms.Button> possédant déjà une représentation graphique que vous ne voulez pas insérer dans votre rendu, vous ne devez pas appeler la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de votre classe de base.  
  
 Le code de la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> s'exécute lorsque le contrôle est dessiné, puis chaque fois qu'il est actualisé.  Pour être sûr que votre contrôle sera redessiné chaque fois qu'il sera redimensionné, ajoutez la ligne suivante à son constructeur :  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
  
```  
  
> [!NOTE]
>  Utilisez la propriété <xref:System.Windows.Forms.Control.Region%2A?displayProperty=fullName> pour implémenter un contrôle non rectangulaire.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.Region%2A>   
 <xref:System.Windows.Forms.ControlStyles>   
 <xref:System.Drawing.Graphics>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 <xref:System.Windows.Forms.PaintEventArgs>   
 [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [Contrôles constitutifs](../../../../docs/framework/winforms/controls/constituent-controls.md)   
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)