---
title: "Comment : lire des métadonnées d'image"
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
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b610e499ff980d2e705ad855ae98c1d54ff412e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-read-image-metadata"></a>Comment : lire des métadonnées d'image
Certains fichiers image contiennent des métadonnées que vous pouvez lire pour déterminer les fonctionnalités de l’image. Par exemple, une photographie numérique peut contenir des métadonnées que vous pouvez lire pour déterminer la marque et le modèle de l’appareil photo utilisé pour capturer l’image. Avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez lire des métadonnées existantes et vous pouvez également écrire de nouvelles métadonnées dans des fichiers image.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]stocke un élément individuel de métadonnées dans un <xref:System.Drawing.Imaging.PropertyItem> objet. Vous pouvez lire la <xref:System.Drawing.Image.PropertyItems%2A> propriété d’un <xref:System.Drawing.Image> objet à récupérer toutes les métadonnées à partir d’un fichier. Le <xref:System.Drawing.Image.PropertyItems%2A> propriété retourne un tableau de <xref:System.Drawing.Imaging.PropertyItem> objets.  
  
 A <xref:System.Drawing.Imaging.PropertyItem> objet possède les quatre propriétés suivantes : `Id`, `Value`, `Len`, et `Type`.  
  
## <a name="id"></a>Id  
 Une balise qui identifie l’élément de métadonnées. Certaines valeurs qui peuvent être affectés à <xref:System.Drawing.Imaging.PropertyItem.Id%2A> sont affichés dans le tableau suivant.  
  
|Valeur hexadécimale|Description|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0 x 0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Titre de l’image<br /><br /> Fabricant de matériel<br /><br /> Modèle de matériel<br /><br /> ExifDTOriginal<br /><br /> Temps d’exposition EXIF<br /><br /> Tableau de luminance<br /><br /> Tableau de chrominance|  
  
## <a name="value"></a>Value  
 Un tableau de valeurs. Le format des valeurs est déterminé par le <xref:System.Drawing.Imaging.PropertyItem.Type%2A> propriété.  
  
## <a name="len"></a>Len  
 La longueur (en octets) du tableau de valeurs vers lequel pointe le <xref:System.Drawing.Imaging.PropertyItem.Value%2A> propriété.  
  
## <a name="type"></a>Type  
 Le type de données des valeurs dans le tableau vers lequel pointe le `Value` propriété. Les formats indiqués par les `Type` des valeurs de propriété sont affichés dans le tableau suivant  
  
|Valeur numérique|Description|  
|-------------------|-----------------|  
|1|`Byte`|  
|2|Un tableau de `Byte` objets encodés en ASCII|  
|3|Un entier 16 bits|  
|4|Un entier 32 bits|  
|5|Un tableau de deux `Byte` objets qui représentent un nombre rationnel|  
|6|Non utilisé|  
|7|Undefined|  
|8|Non utilisé|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple de code suivant lit et affiche les sept des métadonnées dans le fichier `FakePhoto.jpg`. Le deuxième élément de propriété (index 1) dans la liste a <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (fabricant) et <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (tableau d’octets encodé en ASCII). L’exemple de code affiche la valeur de cet élément de propriété.  
  
 Le code produit un résultat similaire au suivant :  
  
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
  
### <a name="code"></a>Code  
 [!code-csharp[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>. Gérer du formulaire <xref:System.Windows.Forms.Control.Paint> événement et collez ce code dans le Gestionnaire d’événements de peinture. Vous devez remplacer `FakePhoto.jpg` avec un nom de l’image et le chemin d’accès valide sur votre système et importer le `System.Drawing.Imaging` espace de noms.  
  
## <a name="see-also"></a>Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
