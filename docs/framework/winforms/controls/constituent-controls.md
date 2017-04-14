---
title: "Contr&#244;les constitutifs | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), contrôles constitutifs"
  - "contrôles utilisateur (Windows Forms), contrôles constitutifs"
  - "UserControl (classe)"
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Contr&#244;les constitutifs
Les contrôles qui composent un contrôle utilisateur, appelés *contrôles constitutifs*, offrent relativement peu de latitude en matière de rendu graphique personnalisé.  Tous les contrôles Windows Forms gèrent leur propre rendu par le biais de leur méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.  Cette méthode étant protégée, elle n'est pas accessible au développeur, et son exécution lorsque le contrôle est peint ne peut donc pas être inhibée.  Toutefois, cela ne vous empêche pas d'ajouter du code affectant l'apparence des contrôles constitutifs.  Il est possible de définir un rendu supplémentaire en ajoutant un gestionnaire d'événements.  Supposons que vous créez <xref:System.Windows.Forms.UserControl> contenant un bouton appelé `MyButton`.  Pour obtenir un autre rendu en plus de celui qui est déjà proposé par la [classe Button](frlrfSystemWebUIWebControlsButtonClassTopic), vous devez ajouter à votre contrôle utilisateur un code similaire à celui\-ci :  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=   
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,   
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
>  Certains contrôles Windows Forms, tels que <xref:System.Windows.Forms.TextBox>, sont directement peints par Windows.  La méthode <xref:System.Windows.Forms.Control.OnPaint%2A> n'est jamais appelée pour ces contrôles ; l'exemple précédent ne peut donc jamais leur être appliqué.  
  
 Cet exemple crée une méthode qui s'exécute chaque fois que s'exécute l'événement `MyButton.Paint`, ce qui ajoute une représentation graphique supplémentaire à votre contrôle.  Notez que cela n'empêche pas la méthode `MyButton.OnPaint` de s'exécuter ; ainsi, vous obtenez toute la peinture habituellement effectuée par un bouton en plus de votre peinture personnalisée.  Pour plus d'informations sur la technologie GDI\+ et le rendu personnalisé, consultez [Création d'images graphiques avec GDI\+](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  Si vous souhaitez donner à votre contrôle une représentation unique, la meilleure façon de procéder est de créer un contrôle hérité et d'écrire pour lui un code de rendu personnalisé.  Pour plus d'informations, consultez [Contrôles dessinés par l'utilisateur](../../../../docs/framework/winforms/controls/user-drawn-controls.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.UserControl>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 [Contrôles dessinés par l'utilisateur](../../../../docs/framework/winforms/controls/user-drawn-controls.md)   
 [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)