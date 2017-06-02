---
title: "Comment&#160;: cr&#233;er une collection de polices priv&#233;es | Microsoft Docs"
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
  - "polices, créer des collections privées"
  - "collections de polices privées, créer"
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: cr&#233;er une collection de polices priv&#233;es
La classe <xref:System.Drawing.Text.PrivateFontCollection> hérite de la classe de base abstraite <xref:System.Drawing.Text.FontCollection>.  Vous pouvez utiliser un objet <xref:System.Drawing.Text.PrivateFontCollection> pour maintenir un ensemble de polices spécifiquement pour votre application.  Une collection de polices privée peut inclure des polices système installées ainsi que des polices qui n'ont pas été installées sur l'ordinateur.  Pour ajouter un fichier de polices à une collection de polices privées, appelez la méthode <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> d'un objet <xref:System.Drawing.Text.PrivateFontCollection>.  
  
 La propriété <xref:System.Drawing.Text.FontCollection.Families%2A> d'un objet <xref:System.Drawing.Text.PrivateFontCollection> contient un tableau d'objets <xref:System.Drawing.FontFamily>.  
  
 Le nombre de familles de polices dans une collection de polices privées n'est pas nécessairement le même que le nombre de fichiers de polices qui ont été ajoutés à la collection.  Par exemple, supposons que vous ajoutiez les fichiers ArialBd.tff, Times.tff et TimesBd.tff à une collection.  La collection comportera trois fichiers mais seulement deux familles puisque que Times.tff et TimesBd.tff appartiennent à la même famille.  
  
## Exemple  
 L'exemple suivant ajoute les trois fichiers de polices suivants à un objet <xref:System.Drawing.Text.PrivateFontCollection> :  
  
-   C:\\*systemroot*\\Fonts\\Arial.tff \(Arial, Normal\)  
  
-   C:\\*systemroot*\\Fonts\\CourBI.tff \(Courier New, Gras Italique\)  
  
-   C:\\*systemroot*\\Fonts\\TimesBd.tff \(Times New Roman, Gras\)  
  
 Le code récupère un tableau d'objets <xref:System.Drawing.FontFamily> de la propriété <xref:System.Drawing.Text.FontCollection.Families%2A> de l'objet <xref:System.Drawing.Text.PrivateFontCollection>.  
  
 Pour chaque objet <xref:System.Drawing.FontFamily> dans la collection, le code appelle la méthode <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> pour déterminer si divers styles \(Regular, Bold, Italic, Bold Italic, Underline et Strikeout\) sont disponibles.  Les arguments passés à la méthode <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> sont des membres de l'énumération <xref:System.Drawing.FontStyle>.  
  
 Si une combinaison famille\/style donnée est disponible, un objet <xref:System.Drawing.Font> est généré en utilisant cette famille et ce style.  Le premier argument passé au constructeur <xref:System.Drawing.Font.%23ctor%2A> est le nom de la famille de polices \(et non un objet <xref:System.Drawing.FontFamily> comme c'est le cas pour d'autres variantes du constructeur <xref:System.Drawing.Font.%23ctor%2A>\).  Une fois l'objet <xref:System.Drawing.Font> construit, il est passé à la méthode <xref:System.Drawing.Graphics.DrawString%2A> de la classe <xref:System.Drawing.Graphics> pour afficher le nom de famille ainsi que le nom du style.  
  
 La sortie du code suivant est analogue à celle qui est présentée dans l'illustration suivante.  
  
 ![Polices du texte](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")  
  
 Arial.tff \(qui a été ajouté à la collection de polices privées dans l'exemple de code suivant\) est le fichier de police pour le style Arial Regular.  Notez toutefois que la sortie du programme montre plusieurs styles disponibles autres que le style Regular pour la famille de polices Arial.  Ceci est dû au fait que [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] peut simuler les styles italique, gras et italique et gras depuis le style normal.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] peut également produire des soulignements et des barrés depuis le style normal.  
  
 De la même façon, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] peut simuler le style italique gras depuis du style gras ou italique.  La sortie du programme montre que le style Bold Italic est disponible pour la famille Times bien que TimesBd.tff \(Times New Roman, bold\) est le seul fichier Times de la collection.  
  
 [!code-csharp[System.Drawing.FontsAndText#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 <xref:System.Drawing.Text.PrivateFontCollection>   
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)