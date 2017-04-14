---
title: "Comment&#160;: lire des m&#233;tadonn&#233;es d&#39;image | Microsoft Docs"
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
  - "métadonnées, élément de propriété"
  - "métadonnées, lire une image"
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: lire des m&#233;tadonn&#233;es d&#39;image
Certains fichiers image contiennent des métadonnées que vous pouvez lire pour déterminer les fonctionnalités de l'image.  Par exemple, une photographie numérique peut contenir des métadonnées que vous pouvez lire pour déterminer la marque et le modèle de l'appareil photo utilisé pour capturer l'image.  Avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez lire des métadonnées existantes et écrire de nouvelles métadonnées dans des fichiers image.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] stocke un élément individuel de métadonnées dans un objet <xref:System.Drawing.Imaging.PropertyItem>.  Vous pouvez lire la propriété <xref:System.Drawing.Image.PropertyItems%2A> d'un objet <xref:System.Drawing.Image> pour récupérer toutes les métadonnées d'un fichier.  La propriété <xref:System.Drawing.Image.PropertyItems%2A> retourne un tableau d'objets <xref:System.Drawing.Imaging.PropertyItem>.  
  
 Un objet <xref:System.Drawing.Imaging.PropertyItem> contient les quatre propriétés suivantes : `Id`, `Value`, `Len` et `Type`.  
  
## Id  
 Balise identifiant la métadonnée.  Certaines valeurs pouvant être assignées à <xref:System.Drawing.Imaging.PropertyItem.Id%2A> sont présentées dans le tableau suivant.  
  
|Valeur hexadécimale|Description|  
|-------------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Titre de l'image<br /><br /> Fabricant de l'équipement<br /><br /> Modèle de l'équipement<br /><br /> ExifDTOriginal<br /><br /> Temps d'exposition Exif<br /><br /> Tableau de luminance<br /><br /> Tableau de chrominance|  
  
## Valeur  
 Tableau de valeurs.  Le format des valeurs est déterminé par la propriété <xref:System.Drawing.Imaging.PropertyItem.Type%2A>.  
  
## Len  
 Longueur \(en octets\) du tableau de valeurs sur lequel pointe la propriété <xref:System.Drawing.Imaging.PropertyItem.Value%2A>.  
  
## Type  
 Type de données des valeurs dans le tableau vers lequel la propriété `Value` pointe.  Les formats indiqués par les valeurs de la propriété `Type` sont présentés dans le tableau suivant.  
  
|Valeur numérique|Description|  
|----------------------|-----------------|  
|1|Un `Byte`|  
|2|Tableau d'objets `Byte` encodés en ASCII|  
|3|Entier 16 bits|  
|4|Entier 32 bits|  
|5|Tableau de deux objets `Byte` qui représentent un nombre rationnel|  
|6|Non utilisé|  
|7|Indéfini|  
|8|Non utilisé|  
|9|`SLong`|  
|10|`SRational`|  
  
## Exemple  
  
### Description  
 L'exemple de code suivant lit et affiche les sept métadonnées du fichier `FakePhoto.jpg`.  Le second élément de la propriété \(index 1\) dans la liste porte <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F \(fabricant de l'équipement\) et <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 \(tableau d'octets encodé en ASCII\).  L'exemple de code affiche la valeur de cet élément de propriété.  
  
 Le code produit une sortie identique à ce qui suit :  
  
 `Property Item 0`  
  
 `id: 0x320`  
  
 `type: 2`  
  
 `length: 16 bytes`  
  
 `Property Item 1`  
  
 `id: 0x10f`  
  
 `type: 2`  
  
 `length: 17 bytes`  
  
 `Property Item 2`  
  
 `id: 0x110`  
  
 `type: 2`  
  
 `length: 7 bytes`  
  
 `Property Item 3`  
  
 `id: 0x9003`  
  
 `type: 2`  
  
 `length: 20 bytes`  
  
 `Property Item 4`  
  
 `id: 0x829a`  
  
 `type: 5`  
  
 `length: 8 bytes`  
  
 `Property Item 5`  
  
 `id: 0x5090`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `Property Item 6`  
  
 `id: 0x5091`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `The equipment make is Northwind Camera.`  
  
### Code  
 [!code-csharp[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  Gérez l'événement <xref:System.Windows.Forms.Control.Paint> du formulaire et collez ce code dans le gestionnaire d'événements Paint.  Vous devez remplacer `FakePhoto.jpg` par un nom d'image et un chemin d'accès valides sur votre système, et importer l'espace de noms `System.Drawing.Imaging`.  
  
## Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)