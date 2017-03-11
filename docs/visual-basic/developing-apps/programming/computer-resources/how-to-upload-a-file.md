---
title: "How to: Upload a File in Visual Basic | Microsoft Docs"
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
  - "networks, uploading files"
  - "files, uploading"
  - "uploading files"
  - "UploadFile method"
  - "My.Computer.Network.UploadFile method"
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# How to: Upload a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

La méthode <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> peut être utilisée pour télécharger un fichier et le stocker dans un emplacement distant.  Si le paramètre `ShowUI` a la valeur `True`, une boîte de dialogue s'affiche pour indiquer la progression du téléchargement et permet aux utilisateurs d'annuler l'opération.  
  
### Pour transférer un fichier  
  
-   Utilisez la méthode `UploadFile` pour transférer un fichier, en spécifiant l'emplacement du fichier source et l'emplacement de répertoire cible sous forme de chaîne ou d'URI. Cet exemple transfère le fichier `Order.txt` vers `http://www.cohowinery.com/uploads.aspx`  
  
     [!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-upload-a-file_1.vb)]  
  
### Pour transférer un fichier et afficher la progression de l'opération  
  
-   Utilisez la méthode `UploadFile` pour transférer un fichier en spécifiant l'emplacement du fichier source et l'emplacement de répertoire cible sous forme de chaîne ou d'URI.  Cet exemple transfère le fichier `Order.txt` vers `http://www.cohowinery.com/uploads.aspx` sans fournir un nom d'utilisateur ou un mot de passe, affiche la progression du transfert et a un intervalle de délai d'attente de 500 millisecondes.  
  
     [!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-upload-a-file_2.vb)]  
  
### Pour transférer un fichier en fournissant un nom d'utilisateur et un mot de passe  
  
-   Utilisez la méthode `UploadFile` pour transférer un fichier en spécifiant l'emplacement du fichier source et l'emplacement du répertoire cible sous forme de chaîne ou d'URI, puis en spécifiant le nom d'utilisateur et le mot de passe.  Cet exemple transfère le fichier `Order.txt` vers `http://www.cohowinery.com/uploads.aspx`en fournissant le nom d'utilisateur `anonymous` et un mot de passe vide.  
  
     [!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-upload-a-file_3.vb)]  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent lever une exception :  
  
-   Le chemin d'accès du fichier local n'est pas valide \(<xref:System.ArgumentException>\).  
  
-   L'authentification a échoué \(<xref:System.Security.SecurityException>\).  
  
-   La connexion a expiré \(<xref:System.TimeoutException>\).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>   
 [How to: Download a File](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)   
 [Comment : analyser des chemins d'accès](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)