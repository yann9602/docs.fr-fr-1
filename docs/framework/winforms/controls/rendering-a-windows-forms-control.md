---
title: "Rendu d'un contrôle Windows Forms"
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
- custom controls [Windows Forms], rendering
- OnPaintBackground method [Windows Forms], invoking in Windows Forms custom controls
- custom controls [Windows Forms], graphics resources
- custom controls [Windows Forms], invalidation and painting
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 587c9c8fb0bf634a2491acb1ae0b2f60979fa899
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="rendering-a-windows-forms-control"></a>Rendu d'un contrôle Windows Forms
Le rendu désigne le processus de création d’une représentation visuelle sur l’écran d’un utilisateur. Windows Forms utilise [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] (la nouvelle bibliothèque de graphiques Windows) pour le rendu. Les classes managées qui donnent accès aux [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] se trouvent dans le <xref:System.Drawing?displayProperty=nameWithType> espace de noms et ses sous-espaces de noms.  
  
 Les éléments suivants sont impliqués dans le rendu du contrôle :  
  
-   Fonctionnalités de dessin fournies par la classe de base <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
-   Les éléments essentiels de la [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] bibliothèque de graphiques.  
  
-   La géométrie de la zone de dessin.  
  
-   La procédure pour libérer les ressources graphiques.  
  
## <a name="drawing-functionality-provided-by-control"></a>La fonctionnalité fournie par le contrôle de dessin  
 La classe de base <xref:System.Windows.Forms.Control> fournit les fonctionnalités de dessin via son <xref:System.Windows.Forms.Control.Paint> événement. Un contrôle déclenche la <xref:System.Windows.Forms.Control.Paint> événement chaque fois qu’il a besoin mettre à jour son affichage. Pour plus d’informations sur les événements dans le .NET Framework, consultez [gestion et déclenchement d’événements](../../../../docs/standard/events/index.md).  
  
 Les données d’événement de classe pour le <xref:System.Windows.Forms.Control.Paint> événement, <xref:System.Windows.Forms.PaintEventArgs>, contient les données nécessaires pour dessiner un contrôle, un handle vers un objet graphics et un objet rectangle qui représente la région à dessiner. Ces objets sont affichés en gras dans le fragment de code suivant.  
  
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
  
 <xref:System.Drawing.Graphics>est une classe managée qui encapsule les fonctionnalités de dessin, tel que décrit dans la discussion de [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] plus loin dans cette rubrique. Le <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> est une instance de la <xref:System.Drawing.Rectangle> structurer et définit la zone disponible dans laquelle un contrôle peut être dessiné. Un développeur de contrôles peut calculer la <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> à l’aide de la <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriété d’un contrôle, comme décrit dans la discussion de géométrie plus loin dans cette rubrique.  
  
 Un contrôle doit fournir la logique de rendu en substituant la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode qu’il hérite <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A>Obtient l’accès à un objet graphics et un rectangle à dessiner via la <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> et <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriétés de la <xref:System.Windows.Forms.PaintEventArgs> instance lui est passé.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 Le <xref:System.Windows.Forms.Control.OnPaint%2A> (méthode) de la base de <xref:System.Windows.Forms.Control> classe n’implémente pas toutes les fonctionnalités de dessin, mais appelle simplement les délégués d’événements qui sont enregistrés avec le <xref:System.Windows.Forms.Control.Paint> événement. Lorsque vous substituez <xref:System.Windows.Forms.Control.OnPaint%2A>, vous devez généralement appeler le <xref:System.Windows.Forms.Control.OnPaint%2A> méthode de la classe de base afin que les délégués inscrits reçoivent le <xref:System.Windows.Forms.Control.Paint> événement. Toutefois, les contrôles qui peignent la totalité de leur surface ne doivent pas appeler de la classe de base <xref:System.Windows.Forms.Control.OnPaint%2A>, car cela entraîne le scintillement. Pour obtenir un exemple de substitution de la <xref:System.Windows.Forms.Control.OnPaint%2A> événements, consultez la [Comment : créer un Windows Forms que montre progression du contrôle](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
>  N’appelez pas <xref:System.Windows.Forms.Control.OnPaint%2A> directement à partir de votre contrôle ; au lieu de cela, appelez le <xref:System.Windows.Forms.Control.Invalidate%2A> (méthode) (héritée de <xref:System.Windows.Forms.Control>) ou une autre méthode qui appelle <xref:System.Windows.Forms.Control.Invalidate%2A>. Le <xref:System.Windows.Forms.Control.Invalidate%2A> méthode appelle à son tour <xref:System.Windows.Forms.Control.OnPaint%2A>. Le <xref:System.Windows.Forms.Control.Invalidate%2A> méthode est surchargée et, selon les arguments fournis à <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, un contrôle redessine une partie ou la totalité de sa zone de l’écran.  
  
 La base de <xref:System.Windows.Forms.Control> classe définit une autre méthode qui est utile pour le dessin, le <xref:System.Windows.Forms.Control.OnPaintBackground%2A> (méthode).  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A>peint l’arrière-plan (et donc la forme) de la fenêtre et est garanti être rapide, tout en <xref:System.Windows.Forms.Control.OnPaint%2A> peint les détails et peut être plus lent, car les demandes de peinture individuelles sont combinées en une seule <xref:System.Windows.Forms.Control.Paint> événement qui couvre tous les domaines qui doivent être redessiné. Vous souhaiterez peut-être appeler le <xref:System.Windows.Forms.Control.OnPaintBackground%2A> si, par exemple, vous souhaitez dessiner un arrière-plan dégradé de couleur pour votre contrôle.  
  
 Alors que <xref:System.Windows.Forms.Control.OnPaintBackground%2A> possède une nomenclature de type événement et prend le même argument que la `OnPaint` (méthode), <xref:System.Windows.Forms.Control.OnPaintBackground%2A> n’est pas une véritable méthode d’événements. Il est sans `PaintBackground` événement et <xref:System.Windows.Forms.Control.OnPaintBackground%2A> n’appelle pas de délégués d’événements. Lors de la substitution du <xref:System.Windows.Forms.Control.OnPaintBackground%2A> méthode, une classe dérivée n’est pas requise pour appeler le <xref:System.Windows.Forms.Control.OnPaintBackground%2A> méthode de sa classe de base.  
  
## <a name="gdi-basics"></a>Principes de base GDI +  
 La <xref:System.Drawing.Graphics> classe fournit des méthodes pour dessiner des formes différentes telles que des cercles, des triangles, des arcs et des ellipses, ainsi que des méthodes pour afficher du texte. Le <xref:System.Drawing?displayProperty=nameWithType> espace de noms et ses sous-espaces de noms contiennent des classes qui encapsulent des éléments graphiques tels que les formes (cercles, rectangles, arcs, etc.), couleurs, polices, pinceaux et ainsi de suite. Pour plus d’informations sur [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], consultez [à l’aide des Classes managées graphiques](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md). L’essentiel de [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] sont également décrites dans le [Comment : créer un Windows Forms que montre progression du contrôle](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Géométrie de la zone de dessin  
 Le <xref:System.Windows.Forms.Control.ClientRectangle%2A> propriété d’un contrôle spécifie la région rectangulaire disponible pour le contrôle sur l’écran de l’utilisateur, tandis que la <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriété du <xref:System.Windows.Forms.PaintEventArgs> spécifie la zone réellement peinte. (N’oubliez pas que peinture est effectuée le <xref:System.Windows.Forms.Control.Paint> méthode événements qui prend un <xref:System.Windows.Forms.PaintEventArgs> instance comme argument). Un contrôle devra peut-être peindre uniquement une partie de sa zone disponible, comme dans le cas lorsqu’une petite section de modifications d’affichage du contrôle. Dans ce cas, un développeur de contrôles doit calculer le rectangle réel pour dessiner dans et passer à <xref:System.Windows.Forms.Control.Invalidate%2A>. Les versions surchargées de <xref:System.Windows.Forms.Control.Invalidate%2A> qui prennent un <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.Region> en tant qu’argument utilisent cet argument pour générer la <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriété du <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Fragment du code suivant montre comment la `FlashTrackBar` contrôle personnalisé calcule la zone rectangulaire à dessiner. Le `client` variable désigne le <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> propriété. Pour obtenir un exemple complet, consultez [Comment : créer un Windows Forms que montre progression du contrôle](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Libération des ressources graphiques  
 Objets graphiques sont coûteux, car ils utilisent des ressources système. Ces objets incluent des instances de la <xref:System.Drawing.Graphics?displayProperty=nameWithType> classe ainsi que les instances de <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>et d’autres classes de graphiques. Il est important de créer une ressource graphique uniquement lorsque vous en avez besoin et libérer dès que vous avez fini de l’utiliser. Si vous créez un type qui implémente le <xref:System.IDisposable> l’interface, appelez sa <xref:System.IDisposable.Dispose%2A> méthode lorsque vous avez terminé de l’utiliser afin de libérer des ressources.  
  
 Fragment du code suivant montre comment la `FlashTrackBar` contrôle personnalisé crée et libère un <xref:System.Drawing.Brush> ressource. Pour le code source complet, consultez [Comment : créer un Windows Forms que montre progression du contrôle](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour créer un contrôle Windows Forms qui affiche la progression](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)
