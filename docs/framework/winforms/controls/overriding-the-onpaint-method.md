---
title: "Substitution de la m&#233;thode OnPaint | Microsoft Docs"
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
  - "OnPaint (méthode), substituer dans les contrôles personnalisés Windows Forms"
  - "Paint (événement), gérer dans les contrôles personnalisés Windows Forms"
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Substitution de la m&#233;thode OnPaint
Les étapes de base de la substitution d'un événement défini dans le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sont identiques et sont récapitulées dans la liste suivante.  
  
#### Pour substituer un événement hérité  
  
1.  Substituez la méthode `On`*NomÉvénement* protégée.  
  
2.  Appelez la méthode `On`*NomÉvénement* de la classe de base à partir de la méthode `On`*NomÉvénement* substituée, de sorte que les délégués inscrits reçoivent l'événement.  
  
 L'événement <xref:System.Windows.Forms.Control.Paint> est décrit en détail dans cette section, car tous les contrôles Windows Forms doivent substituer l'événement <xref:System.Windows.Forms.Control.Paint> qu'ils héritent de <xref:System.Windows.Forms.Control>.  La classe <xref:System.Windows.Forms.Control> de base ignore comment un contrôle dérivé doit être dessiné et ne fournit pas de logique de peinture dans la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.  La méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de la classe <xref:System.Windows.Forms.Control> distribue simplement l'événement <xref:System.Windows.Forms.Control.Paint> aux récepteurs d'événements inscrits.  
  
 Si vous avez utilisé l'exemple dans [Comment : développer un contrôle Windows Forms simple](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), vous avez consulté un exemple de substitution de la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.  Le fragment de code suivant est extrait de cet exemple.  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class   
```  
  
```csharp  
public class FirstControl : Control{  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 La classe <xref:System.Windows.Forms.PaintEventArgs> contient les données de l'événement <xref:System.Windows.Forms.Control.Paint>.  Elle possède deux propriétés, comme illustré dans le code suivant.  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property   
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> est le rectangle à peindre, et la propriété <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> fait référence à un objet <xref:System.Drawing.Graphics>.  Les classes de l'espace de noms <xref:System.Drawing?displayProperty=fullName> sont des classes managées qui permettent d'accéder aux fonctionnalités de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], la nouvelle bibliothèque de graphiques Windows.  L'objet <xref:System.Drawing.Graphics> possède des méthodes pour le dessin de points, de chaînes, de lignes, d'arcs, d'ellipses et de nombreuses autres formes.  
  
 Un contrôle appelle sa méthode <xref:System.Windows.Forms.Control.OnPaint%2A> chaque fois qu'il doit modifier son affichage visuel.  Cette méthode déclenche à son tour l'événement <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Événements](../../../../docs/standard/events/index.md)   
 [Rendu d'un contrôle Windows Forms](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)   
 [Définition d'un événement](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)