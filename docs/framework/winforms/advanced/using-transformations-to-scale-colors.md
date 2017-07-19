---
title: "Utilisation de transformations pour mettre &#224; l&#39;&#233;chelle des couleurs | Microsoft Docs"
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
  - "couleurs, mettre à l'échelle"
  - "transformations, pour mettre les couleurs à l'échelle"
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Utilisation de transformations pour mettre &#224; l&#39;&#233;chelle des couleurs
Une transformation par ajustement multiplie une ou plusieurs des quatre composantes de couleur par un nombre.  Les entrées de la matrice de couleurs représentant l'ajustement sont présentées dans le tableau suivant.  
  
|Composante à ajuster|Entrée de la matrice|  
|--------------------------|--------------------------|  
|Rouge|\[0\]\[0\]|  
|Vert|\[1\]\[1\]|  
|Bleu|\[2\]\[2\]|  
|Alpha|\[3\]\[3\]|  
  
## Mise à l'échelle d'une couleur  
 L'exemple suivant construit un objet <xref:System.Drawing.Image> à partir du fichier ColorBars2.bmp.  Le code met ensuite à l'échelle le composant bleu de chaque pixel de l'image selon un facteur de 2.  L'image d'origine est dessinée le long de l'image transformée.  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 L'illustration suivante montre l'image d'origine sur la gauche et l'image ajustée sur la droite.  
  
 ![Mise à l'échelle des couleurs](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")  
  
 Le tableau suivant dresse la liste des vecteurs de couleurs pour les quatre barres situées de part et d'autre de l'ajustement du bleu.  Notez que la composante bleu située sur la quatrième barre de couleurs est passée de 0,8 à 0,6.  Cela est dû au fait que [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] conserve uniquement la partie fractionnaire du résultat.  Par exemple, \(2\)\(0,8\) \= 1,6 et la partie fractionnaire de 1,6 est 0,6.  Conserver uniquement la partie fractionnaire garantit que le résultat se trouve toujours dans l'intervalle \[0, 1\].  
  
|D'origine|Ajustée|  
|---------------|-------------|  
|\(0.4, 0.4, 0.4, 1\)|\(0.4, 0.4, 0.8, 1\)|  
|\(0.4, 0.2, 0.2, 1\)|\(0.4, 0.2, 0.4, 1\)|  
|\(0.2, 0.4, 0.2, 1\)|\(0.2, 0.4, 0.4, 1\)|  
|\(0.4, 0.4, 0.8, 1\)|\(0.4, 0.4, 0.6, 1\)|  
  
## Mise à l'échelle de plusieurs couleurs  
 L'exemple suivant construit un objet <xref:System.Drawing.Image> à partir du fichier ColorBars2.bmp.  Ensuite, le code ajuste les composantes rouge, vert et bleu de chaque pixel de l'image.  Les composantes rouge sont ajustées par une diminution de 25 pour cent, les composantes vert par une diminution de 35 pour cent et les composantes bleu par une diminution de 50 pour cent.  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 L'illustration suivante montre l'image d'origine sur la gauche et l'image ajustée sur la droite.  
  
 ![Mise à l'échelle des couleurs](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")  
  
 Le tableau suivant dresse la liste des vecteurs de couleurs pour les quatre barres situées de part et d'autre de l'ajustement du rouge, du vert et du bleu.  
  
|D'origine|Ajustée|  
|---------------|-------------|  
|\(0.6, 0.6, 0.6, 1\)|\(0.45, 0.39, 0.3, 1\)|  
|\(0, 1, 1, 1\)|\(0, 0.65, 0.5, 1\)|  
|\(1, 1, 0, 1\)|\(0.75, 0.65, 0, 1\)|  
|\(1, 0, 1, 1\)|\(0.75, 0, 0.5, 1\)|  
  
## Voir aussi  
 <xref:System.Drawing.Imaging.ColorMatrix>   
 <xref:System.Drawing.Imaging.ImageAttributes>   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Recoloriage des images](../../../../docs/framework/winforms/advanced/recoloring-images.md)