---
title: "How to: Read From Binary Files in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "binary files, reading from"
  - "I/O [Visual Basic], reading from binary files"
  - "ReadAllBytes method, reading from binary files"
  - "My.Computer.FileSystem object, reading from binary files"
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Read From Binary Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

L'objet `My.Computer.FileSystem` fournit la méthode `ReadAllBytes` pour la lecture de fichiers binaires.  
  
### Pour lire un fichier binaire  
  
-   Utilisez la méthode `ReadAllBytes` qui retourne le contenu d'un fichier sous forme de tableau d'octets.  Cet exemple montre comment lire le fichier `C:/Documents and Settings/selfportrait.jpg`.  
  
     [!code-vb[VbVbcnMyFileSystem#78](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-binary-_1.vb)]  
  
-   Pour les fichiers binaires volumineux, vous pouvez utiliser la méthode <xref:System.IO.FileStream.Read%2A> de l'objet <xref:System.IO.FileStream> pour lire uniquement une certaine partie du fichier à la fois.  Vous pouvez ensuite limiter la partie du fichier chargée en mémoire pour chaque opération de lecture.  L'exemple de code suivant copie un fichier et permet à l'appelant de spécifier la partie du fichier à lire en mémoire pour chaque opération de lecture.  
  
     [!code-vb[VbVbcnMyFileSystem#91](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-binary-_2.vb)]  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent lever une exception :  
  
-   Le chemin d'accès n'est pas valide pour une des raisons suivantes : il s'agit d'une chaîne de longueur nulle ; il ne contient que des espaces blancs ; il contient des caractères non valides ou il s'agit d'un chemin d'accès d'appareil \(<xref:System.ArgumentException>\).  
  
-   Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   Le fichier n'existe pas \(<xref:System.IO.FileNotFoundException>\).  
  
-   Le fichier est utilisé par un autre processus, ou une erreur E\/S se produit \(<xref:System.IO.IOException>\).  
  
-   Le chemin d'accès dépasse la longueur maximale définie par le système \(<xref:System.IO.PathTooLongException>\).  
  
-   Un nom de fichier ou de répertoire du chemin d'accès contient un signe deux\-points \(:\) ou n'a pas un format correct \(<xref:System.NotSupportedException>\).  
  
-   Il n'y a pas assez de mémoire pour écrire la chaîne dans la mémoire tampon \(<xref:System.OutOfMemoryException>\).  
  
-   L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès \(<xref:System.Security.SecurityException>\).  
  
 Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu.  Par exemple, il se peut qu'un fichier nommé Form1.vb ne soit pas un fichier source Visual Basic.  
  
 Vérifiez toutes les entrées avant d'utiliser les données dans votre application.  Le fichier n'a peut\-être pas le contenu attendu, et les méthodes utilisées pour lire le fichier peuvent échouer.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>   
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Storing Data to and Reading from the Clipboard](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)