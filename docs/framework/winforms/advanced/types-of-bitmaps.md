---
title: "Types de bitmaps | Microsoft Docs"
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
  - "fichiers .bmp"
  - "fichiers .gif"
  - "fichiers .jpeg"
  - "bitmaps (Windows Forms), format de fichier"
  - "Exchangeable Image File (EXIF)"
  - "EXIF (format de fichier)"
  - "fichiers gif"
  - "graphiques (Windows Forms), formats de fichiers"
  - "Format GIF"
  - "images (Windows Forms), formats de fichiers"
  - "Joint Photographic Experts Group (JPEG)"
  - "fichiers jpeg"
  - "images, formats de fichiers"
  - "fichiers PNG"
  - "Format PNG"
  - "Format TIFF"
  - "fichiers TIFF"
ms.assetid: 6be085a2-2c13-47c8-b80a-c18b32777d8d
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Types de bitmaps
Une bitmap est un tableau de bits qui spécifient la couleur de chaque pixel dans un tableau rectangulaire de pixels.  Le nombre de bits associés à un pixel donné détermine le nombre de couleurs pouvant être assignées à ce pixel.  Par exemple, si chaque pixel est représenté par 4 bits, 16 couleurs différentes \(2^4 \= 16\) peuvent être assignées à un pixel donné.  Le tableau suivant donne quelques exemples du nombre de couleurs pouvant être assignées à un pixel représenté par un nombre donné de bits.  
  
|Bits par pixel|Nombre de couleurs pouvant être assignées à un pixel|  
|--------------------|----------------------------------------------------------|  
|1|2^1 \= 2|  
|2|2^2 \= 4|  
|4|2^4 \= 16|  
|8|2^8 \= 256|  
|16|2^16 \= 65,536|  
|24|2^24 \= 16,777,216|  
  
 Les fichiers disque qui stockent des bitmaps contiennent généralement un ou plusieurs blocs d'informations qui indiquent notamment le nombre de bits par pixel, le nombre de pixels contenus dans chaque ligne et le nombre de lignes du tableau.  Un tel fichier peut également comprendre une table des couleurs \(parfois appelée palette de couleurs\).  Une table des couleurs associe des couleurs spécifiques aux nombres composant la bitmap.  L'illustration suivante représente une image agrandie avec sa bitmap et sa table des couleurs.  Chaque pixel est représenté par un nombre de 4 bits, ce qui donne 2^4 \= 16 couleurs dans la table des couleurs.  Chacune des couleurs de la table est représentée par un nombre de 24 bits : 8 bits pour le rouge, 8 bits pour le vert et 8 bits pour le bleu.  Les nombres sont exprimés au format hexadécimal \(base 16\) : A \= 10, B \= 11, C \= 12, D \= 13, E \= 4, F \= 15.  
  
 ![Exemple de bitmap](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art01.png "AboutGdip03\_Art01")  
  
 Examinons le pixel situé ligne 3, colonne 5 dans l'image.  Le nombre correspondant dans la bitmap est 1.  La table des couleurs nous dit que 1 représente la couleur rouge, donc le pixel est rouge.  Toutes les entrées de la ligne du haut de la bitmap sont égales à 3.  La table des couleurs nous dit que 3 représente le bleu, donc tous les pixels de la ligne du haut de l'image sont bleus.  
  
> [!NOTE]
>  Certaines bitmaps sont stockées selon un format de bas en haut : les nombres indiqués dans la première ligne de la bitmap correspondent aux pixels de la ligne du bas de l'image.  
  
 Une bitmap qui stocke des index vers une table des couleurs est dite indexée sur une palette.  Certaines bitmaps n'ont pas besoin de table des couleurs.  Par exemple, si une bitmap utilise 24 bits par pixel, elle peut stocker les couleurs elles\-mêmes plutôt que des index vers une table des couleurs.  L'illustration suivante représente une bitmap qui stocke directement les couleurs \(24 bits par pixel\) au lieu d'utiliser une table des couleurs.  L'illustration présente également une vue agrandie de l'image correspondante.  Dans la bitmap, FFFFFF représente le blanc, FF0000 le rouge, 00FF00 le vert et 0000FF le bleu.  
  
 ![Exemple de bitmap](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art02.png "AboutGdip03\_Art02")  
  
## Formats de fichier graphique  
 Il existe de nombreux formats standard permettant d'enregistrer des bitmaps dans des fichiers sur disque.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] prend en charge les formats de fichiers graphiques décrits dans les paragraphes suivants.  
  
### BMP  
 BMP est un format standard utilisé par Windows pour stocker des images indépendantes des périphériques et des applications.  Le nombre de bits par pixel \(1, 4, 8, 15, 24, 32 ou 64\) pour un fichier BMP donné est spécifié dans l'en\-tête du fichier.  Les fichiers BMP dotés de 24 bits par pixel sont courants.  Les fichiers BMP ne sont normalement pas compressés ; ils sont donc bien adaptés aux transferts sur Internet.  
  
### GIF \(Graphics Interchange Format\)  
 GIF est un format courant pour les images qui figurent dans les pages Web.  Les fichiers GIF sont particulièrement adaptés aux dessins constitués de traits, aux images contenant des blocs de couleur unie et aux images dont les couleurs sont nettement délimitées.  Ils sont compressés, mais aucune information n'est perdue au cours du processus de compression ; ainsi, une image décompressée est exactement identique à l'image d'origine.  Dans un fichier GIF, une couleur peut être définie comme transparente ; dans ce cas, l'image a la couleur d'arrière\-plan de la page Web qui l'affiche.  Une séquence d'images GIF peut être stockée dans un fichier unique pour former une image GIF animée.  Les fichiers GIF stockent au maximum 8 bits par pixel ; ils sont donc limités à 256 couleurs.  
  
### JPEG \(Joint Photographic Experts Group\)  
 JPEG est un modèle de compression qui donne de bons résultats avec les scènes naturelles \(photographies numérisées notamment\).  Quelques informations sont perdues au cours du processus de compression, mais ces pertes sont souvent imperceptibles pour l'œil humain.  Les fichiers JPEG stockent 24 bits par pixel, ce qui leur permet d'afficher plus de 16 millions de couleurs.  Les fichiers JPEG ne prennent en charge ni la transparence ni l'animation.  
  
 Le niveau de compression des images JPEG est configurable, mais les niveaux de compression élevés \(fichiers de plus petite taille\) entraînent une plus grande perte d'informations.  Un taux de compression 20:1 produit souvent une image que l'œil humain a du mal à distinguer de l'image d'origine.  L'illustration suivante représente une image BMP et deux images JPEG compressées à partir de cette image BMP.  Le taux de compression est 4:1 pour la première image JPEG et 8:1 \(environ\) pour la seconde.  
  
 ![Exemples de types de fichiers](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03.gif "AboutGdip03\_Art03")  
  
 La compression JPEG n'est pas bien adaptée aux dessins constitués de traits, aux blocs de couleur unie et aux couleurs nettement délimitées.  L'illustration suivante représente une image BMP ainsi que deux images JPEG et une image GIF.  Les images JPEG et GIF ont été compressées à partir de l'image BMP.  Le taux de compression est 4:1 pour l'image GIF, 4:1 pour la plus petite image JPEG et 8:3 pour la plus grande image JPEG.  Notez que l'image GIF conserve la netteté des limites le long des traits alors que les images JPEG ont tendance à brouiller les limites.  
  
 ![Types de fichiers](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03a.png "AboutGdip03\_Art03A")  
  
 JPEG est un modèle de compression et non un format de fichier.  Le format d'échange de fichiers JPEG \(JFIF, JPEG File Interchange Format\) est couramment utilisé pour stocker et transférer des images qui ont été compressées selon le modèle JPEG.  Les fichiers JFIF affichés par les navigateurs Web utilisent l'extension .jpg.  
  
### EXIF \(Exchangeable Image File\)  
 EXIF est un format de fichier utilisé pour les photographies capturées par des appareils photo numériques.  Un fichier EXIF contient une image qui a été compressée conformément à la spécification JPEG.  Un fichier EXIF contient également des informations sur la photographie \(date de prise, vitesse d'obturation, temps d'exposition, etc.\) et sur l'appareil photo \(fabricant, modèle, etc.\).  
  
### PNG \(Portable Network Graphics\)  
 Le format PNG présente de nombreux avantages du format GIF, avec des fonctionnalités supplémentaires.  Comme les fichiers GIF, les fichiers PNG sont compressés sans aucune perte d'informations.  Les fichiers PNG peuvent stocker des couleurs avec 8, 24 ou 48 bits par pixel et des nuances de gris avec 1, 2, 4, 8 ou 16 bits par pixel.  Les fichiers GIF ne peuvent quant à eux stocker que 1, 2, 4 ou 8 bits par pixel.  Un fichier PNG peut également stocker une valeur alpha pour chaque pixel ; cette valeur spécifie le degré de fusion entre la couleur du pixel en question et la couleur de l'arrière\-plan.  
  
 Le format PNG surpasse le format GIF par sa capacité à afficher progressivement une image, c'est\-à\-dire à afficher des approximations de plus en plus exactes de l'image à mesure de sa transmission via une connexion réseau.  Les fichiers PNG peuvent contenir des informations de correction gamma et de correction des couleurs assurant un rendu correct des images sur différents périphériques d'affichage.  
  
### TIFF \(Tag Image File Format\)  
 TIFF est un format à la fois souple et extensible, qui est pris en charge par un grand nombre de plateformes et d'applications de traitement d'images.  Les fichiers TIFF peuvent stocker des images comportant un nombre arbitraire de bits par pixel et utiliser différents algorithmes de compression.  Plusieurs images peuvent être stockées dans un seul fichier TIFF de plusieurs pages.  Les informations qui concernent l'image \(marque de scanneur, ordinateur hôte, type de compression, orientation, échantillons par pixel, etc.\) peuvent être stockées dans le fichier et organisées à l'aide de balises.  Si nécessaire, le format TIFF peut être étendu par l'ajout \(suite à approbation\) de nouvelles balises.  
  
## Voir aussi  
 <xref:System.Drawing.Image?displayProperty=fullName>   
 <xref:System.Drawing.Bitmap?displayProperty=fullName>   
 <xref:System.Drawing.Imaging.PixelFormat?displayProperty=fullName>   
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)