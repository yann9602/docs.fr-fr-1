---
title: "Comment : créer une collection de polices privées"
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
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c0107b1ef1d5259835c6fb1666519d3fc06f4e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-private-font-collection"></a>Comment : créer une collection de polices privées
Le <xref:System.Drawing.Text.PrivateFontCollection> classe hérite de la <xref:System.Drawing.Text.FontCollection> classe de base abstraite. Vous pouvez utiliser un <xref:System.Drawing.Text.PrivateFontCollection> objet de conserver un jeu de polices spécifiquement pour votre application. Une collection de polices privées peut inclure des polices système installées ainsi que des polices qui n’ont pas été installées sur l’ordinateur. Pour ajouter un fichier de polices à une collection de polices privées, appelez le <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> méthode d’un <xref:System.Drawing.Text.PrivateFontCollection> objet.  
  
 Le <xref:System.Drawing.Text.FontCollection.Families%2A> propriété d’un <xref:System.Drawing.Text.PrivateFontCollection> objet contient un tableau de <xref:System.Drawing.FontFamily> objets.  
  
 Le nombre de familles de polices dans une collection de polices privées n’est pas nécessairement le même que le nombre de fichiers de polices qui ont été ajoutés à la collection. Par exemple, supposons que vous ajoutez les fichiers ArialBd.tff, Times.tff et TimesBd.tff à une collection. Il y aura trois fichiers mais seulement deux familles dans la collection, car Times.tff et TimesBd.tff appartiennent à la même famille.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant ajoute les fichiers de trois police suivants pour un <xref:System.Drawing.Text.PrivateFontCollection> objet :  
  
-   C:\\*systemroot*\Fonts\Arial.tff (Arial, normal)  
  
-   C:\\*systemroot*\Fonts\CourBI.tff (Courier New, gras et italique)  
  
-   C:\\*systemroot*\Fonts\TimesBd.tff (Times New Roman, gras)  
  
 Le code récupère un tableau de <xref:System.Drawing.FontFamily> des objets de la <xref:System.Drawing.Text.FontCollection.Families%2A> propriété de la <xref:System.Drawing.Text.PrivateFontCollection> objet.  
  
 Pour chaque <xref:System.Drawing.FontFamily> objet dans la collection, le code appelle la <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> méthode pour déterminer si divers styles (Normal, gras, italique, gras et italique, souligné et barré) sont disponibles. Les arguments passés à la <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> méthode sont membres de la <xref:System.Drawing.FontStyle> énumération.  
  
 Si une combinaison famille/style donnée est disponible, un <xref:System.Drawing.Font> objet est construit à l’aide de cette famille et ce style. Le premier argument passé à la <xref:System.Drawing.Font.%23ctor%2A> constructeur est le nom de famille de polices (pas un <xref:System.Drawing.FontFamily> de l’objet comme c’est le cas pour d’autres variantes de la <xref:System.Drawing.Font.%23ctor%2A> constructeur). Après le <xref:System.Drawing.Font> objet est construit, il est passé à la <xref:System.Drawing.Graphics.DrawString%2A> méthode de la <xref:System.Drawing.Graphics> classe pour afficher le nom de famille, ainsi que le nom du style.  
  
 La sortie du code suivant est semblable à la sortie affichée dans l’illustration suivante.  
  
 ![Polices du texte](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")  
  
 Arial.tff (qui a été ajouté à la collection de polices privées dans l’exemple de code suivant) est le fichier de police pour le style Arial regular. Toutefois, notez que la sortie du programme montre plusieurs styles disponibles que regular pour la famille de polices Arial. C’est parce que [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] peut simuler les styles italique gras, italique et gras depuis le style Normal. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]peut également produire des soulignements et des barrés depuis le style Normal.  
  
 De même, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] peut simuler le style gras et italique à partir du style gras ou italique. La sortie du programme montre que le style italique gras est disponible pour la famille Times bien que TimesBd.tff (Times New Roman, gras) est le seul fichier Times de la collection.  
  
 [!code-csharp[System.Drawing.FontsAndText#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
