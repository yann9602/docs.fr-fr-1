---
title: "Rendu d&#39;un contr&#244;le Windows Forms | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), ressources graphiques"
  - "contrôles personnalisés (Windows Forms), invalidation et peinture"
  - "contrôles personnalisés (Windows Forms), rendu"
  - "OnPaintBackground (méthode), appeler dans les contrôles personnalisés Windows Forms"
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Rendu d&#39;un contr&#244;le Windows Forms
Le rendu désigne le processus de création d'une représentation visuelle sur l'écran de l'utilisateur.  Windows Forms utilise [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] \(la nouvelle bibliothèque de graphiques Windows\) pour le rendu.  Les classes managées qui donnent accès à [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] se trouvent dans l'espace de noms <xref:System.Drawing?displayProperty=fullName> et ses sous\-espaces de noms.  
  
 Les éléments suivants sont impliqués dans le rendu du contrôle :  
  
-   Fonctionnalités de dessin fournies par la classe de base <xref:System.Windows.Forms.Control?displayProperty=fullName>.  
  
-   Éléments essentiels de la bibliothèque de graphiques [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
-   Géométrie de la région de dessin.  
  
-   Procédure permettant de libérer les ressources graphiques.  
  
## Fonctionnalités de dessin fournies par le contrôle  
 La classe de base <xref:System.Windows.Forms.Control> fournit des fonctionnalités de dessin à l'aide de son événement <xref:System.Windows.Forms.Control.Paint>.  Un contrôle déclenche l'événement <xref:System.Windows.Forms.Control.Paint> chaque fois qu'il doit mettre à jour son affichage.  Pour plus d'informations sur les événements dans le .NET Framework, consultez [Gestion et déclenchement d'événements](../../../../docs/standard/events/index.md).  
  
 La classe de données d'événement de l'événement <xref:System.Windows.Forms.Control.Paint>, <xref:System.Windows.Forms.PaintEventArgs>, contient les données nécessaires pour le dessin d'un contrôle, c'est\-à\-dire un handle d'un objet de graphiques et d'un objet de rectangle qui représente la région à dessiner.  Ces objets sont affichés en gras dans le fragment de code suivant.  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   Implements IDisposable  
  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property  
   ' Other properties and methods.  
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs, IDisposable {  
public System.Drawing.Rectangle ClipRectangle {get;}  
public System.Drawing.Graphics Graphics {get;}  
// Other properties and methods.  
...  
}  
```  
  
 <xref:System.Drawing.Graphics> est une classe managée qui encapsule les fonctionnalités de dessin, telles qu'elles sont décrites dans l'explication de [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], plus loin dans cette rubrique.  <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> est une instance de la classe <xref:System.Drawing.Rectangle> et définit la zone disponible dans laquelle un contrôle peut être dessiné.  Un développeur de contrôles peut calculer <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> à l'aide de la propriété <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> d'un contrôle, comme décrit dans l'explication de la géométrie, plus loin dans cette rubrique.  
  
 Un contrôle doit fournir une logique de rendu en substituant la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> qu'il hérite de <xref:System.Windows.Forms.Control>.  <xref:System.Windows.Forms.Control.OnPaint%2A> obtient l'accès à un objet Graphics et à un rectangle dans lequel dessiner via les propriétés <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> et <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> de l'instance <xref:System.Windows.Forms.PaintEventArgs> qui lui est passée.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 La méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de la classe <xref:System.Windows.Forms.Control> de base n'implémente aucune fonctionnalité de dessin, mais appelle simplement les délégués d'événement inscrits auprès de l'événement <xref:System.Windows.Forms.Control.Paint>.  Lorsque vous substituez <xref:System.Windows.Forms.Control.OnPaint%2A>, vous devez généralement appeler la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de la classe de base de sorte que les délégués inscrits reçoivent l'événement <xref:System.Windows.Forms.Control.Paint>.  Cependant, les contrôles qui peignent la totalité de leur surface ne doivent pas appeler la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de la classe de base, car cela entraîne du scintillement.  Pour obtenir un exemple de substitution de l'événement <xref:System.Windows.Forms.Control.OnPaint%2A>, consultez le [Comment : créer un contrôle Windows Forms qui affiche la progression](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
>  N'appelez pas <xref:System.Windows.Forms.Control.OnPaint%2A> directement à partir de votre contrôle. Appelez plutôt la méthode <xref:System.Windows.Forms.Control.Invalidate%2A> \(héritée de <xref:System.Windows.Forms.Control>\) ou toute autre méthode appelant <xref:System.Windows.Forms.Control.Invalidate%2A>.  La méthode <xref:System.Windows.Forms.Control.Invalidate%2A> appelle à son tour <xref:System.Windows.Forms.Control.OnPaint%2A>.  La méthode <xref:System.Windows.Forms.Control.Invalidate%2A> est surchargée et, selon les arguments fournis à <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, un contrôle redessine une partie ou la totalité de sa zone d'affichage.  
  
 La classe <xref:System.Windows.Forms.Control> de base définit une autre méthode utile pour le dessin : la méthode <xref:System.Windows.Forms.Control.OnPaintBackground%2A>.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> peint l'arrière\-plan \(et donc la forme\) de la fenêtre et sa rapidité est garantie, alors que <xref:System.Windows.Forms.Control.OnPaint%2A> peint les détails et peut être plus lent, car les demandes de peinture individuelles sont combinées dans un événement <xref:System.Windows.Forms.Control.Paint> qui couvre toutes les zones à redessiner.  Il est possible d'appeler <xref:System.Windows.Forms.Control.OnPaintBackground%2A> si, par exemple, vous souhaitez dessiner un arrière\-plan en couleurs dégradées pour votre contrôle.  
  
 Alors que <xref:System.Windows.Forms.Control.OnPaintBackground%2A> possède une nomenclature de type événement et prend le même argument que la méthode `OnPaint`, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> n'est pas une véritable méthode d'événements.  Il n'existe aucun événement `PaintBackground` et <xref:System.Windows.Forms.Control.OnPaintBackground%2A> n'appelle pas de délégués d'événements.  Lors de la substitution de la méthode <xref:System.Windows.Forms.Control.OnPaintBackground%2A>, une classe dérivée n'est pas obligée d'appeler la méthode <xref:System.Windows.Forms.Control.OnPaintBackground%2A> de sa classe de base.  
  
## Concepts de base de GDI\+  
 La classe <xref:System.Drawing.Graphics> fournit des méthodes pour le dessin de diverses formes, telles que des cercles, des triangles, des arcs et des ellipses, ainsi que des méthodes pour l'affichage de texte.  L'espace de noms <xref:System.Drawing?displayProperty=fullName> et ses sous\-espaces de noms contiennent des classes qui encapsulent des éléments graphiques, tels que des formes \(cercles, rectangles, arcs, etc.\), des couleurs, des polices, des pinceaux, etc.  Pour plus d'informations sur [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], consultez [Utilisation de classes graphiques managées](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md).  Les qualités indispensables de [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] sont également décrites dans le [Comment : créer un contrôle Windows Forms qui affiche la progression](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## Géométrie de la région de dessin  
 La propriété <xref:System.Windows.Forms.Control.ClientRectangle%2A> d'un contrôle spécifie la région rectangulaire mise à la disposition du contrôle sur l'écran de l'utilisateur, alors que la propriété <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> de <xref:System.Windows.Forms.PaintEventArgs> spécifie la zone réellement peinte.  \(N'oubliez pas que la peinture est effectuée dans la méthode <xref:System.Windows.Forms.Control.Paint> qui prend comme argument une instance de <xref:System.Windows.Forms.PaintEventArgs>.\)  Il se peut qu'un contrôle ne doive peindre qu'une partie de sa zone disponible, comme c'est le cas lorsqu'une petite section de l'affichage du contrôle est modifiée.  Dans ce cas, un développeur de contrôles doit calculer le rectangle réel dans lequel effectuer le dessin et le passer à <xref:System.Windows.Forms.Control.Invalidate%2A>.  Les versions surchargées de <xref:System.Windows.Forms.Control.Invalidate%2A> qui prend un <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.Region> comme argument utilisent cet argument pour générer la propriété <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> de <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Le fragment de code suivant montre la manière dont le contrôle personnalisé `FlashTrackBar` calcule la zone rectangulaire dans laquelle dessiner.  La variable `client` indique la propriété <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>.  Pour l'exemple complet, consultez [Comment : créer un contrôle Windows Forms qui affiche la progression](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## Libération des ressources graphiques  
 Les objets graphiques sont coûteux, car ils utilisent les ressources système.  De tels objets incluent des instances de la classe <xref:System.Drawing.Graphics?displayProperty=fullName> aussi bien que des instances de <xref:System.Drawing.Brush?displayProperty=fullName>, <xref:System.Drawing.Pen?displayProperty=fullName> et d'autres classes de graphiques.  Veillez à ne créer une ressource graphique qu'en cas de nécessité et à la libérer dès que vous avez terminé de l'utiliser.  Si vous créez un type qui implémente l'interface <xref:System.IDisposable>, appelez sa méthode <xref:System.IDisposable.Dispose%2A> lorsque vous avez terminé de l'utiliser afin de libérer des ressources.  
  
 Le fragment de code suivant montre comment le contrôle personnalisé `FlashTrackBar` crée et libère une ressource <xref:System.Drawing.Brush>.  Pour le code source complet, consultez [Comment : créer un contrôle Windows Forms qui affiche la progression](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## Voir aussi  
 [Comment : créer un contrôle Windows Forms qui affiche la progression](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)