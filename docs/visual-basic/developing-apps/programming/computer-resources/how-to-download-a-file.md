---
title: "How to: Download a File in Visual Basic | Microsoft Docs"
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
  - "downloading Internet resources, files"
  - "downloading files"
  - "remote computers, downloading from"
  - "files, downloading"
  - "files, transferring"
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# How to: Download a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

La méthode <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> peut être utilisée pour télécharger un fichier distant et le stocker dans un emplacement spécifique.  Si le paramètre `ShowUI` a la valeur `True`, une boîte de dialogue s'affiche pour indiquer la progression du téléchargement et permettre aux utilisateurs d'annuler l'opération.  Par défaut, les fichiers existants portant le même nom ne sont pas remplacés ; si vous souhaitez le faire, affectez le paramètre `overwrite` à `True`.  
  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le nom du lecteur est incorrect \(<xref:System.ArgumentException>\).  
  
-   L'authentification nécessaire n'a pas été fournie \(<xref:System.UnauthorizedAccessException> ou <xref:System.Security.SecurityException>\).  
  
-   Le serveur ne répond pas dans le `connectionTimeout` spécifié \(<xref:System.TimeoutException>\).  
  
-   La demande est refusée par le site Web \(<xref:System.Net.WebException>\).  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu.  Par exemple, il se peut qu'un fichier nommé Form1.vb ne soit pas un fichier source Visual Basic.  Vérifiez toutes les entrées avant d'utiliser les données dans votre application.  Le fichier n'a peut\-être pas le contenu attendu, et les méthodes utilisées pour lire le fichier peuvent échouer.  
  
### Pour télécharger un fichier  
  
-   Utilisez la méthode `DownloadFile` pour télécharger le fichier, en spécifiant l'emplacement du fichier cible sous forme de chaîne ou d'URI et en spécifiant l'emplacement dans lequel stocker le fichier.  Cet exemple télécharge le fichier `WineList.txt` à partir de `http://www.cohowinery.com/downloads` et l'enregistre dans `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-download-a-file_1.vb)]  
  
### Pour télécharger un fichier en spécifiant un délai d'attente  
  
-   Utilisez la méthode `DownloadFile` pour télécharger le fichier en spécifiant l'emplacement du fichier cible sous forme de chaîne ou d'URI, en spécifiant l'emplacement dans lequel stocker le fichier et en spécifiant le délai d'attente en millisecondes \(la valeur par défaut étant de 1000\).  Cet exemple télécharge le fichier `WineList.txt` à partir du site `http://www.cohowinery.com/downloads` et le sauvegarde dans `C:\Documents and Settings\All Users\Documents` en spécifiant un délai d'attente de 500 millisecondes :  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-download-a-file_2.vb)]  
  
### Pour télécharger un fichier en fournissant un nom d'utilisateur et un mot de passe  
  
-   Utilisez la méthode `DownLoadFile` pour télécharger le fichier, en spécifiant l'emplacement du fichier cible sous forme de chaîne ou d'URI et en spécifiant l'emplacement dans lequel stocker le fichier, le nom d'utilisateur et le mot de passe.  Cet exemple télécharge le fichier `WineList.txt` à partir du site `http://www.cohowinery.com/downloads` et le sauvegarde dans `C:\Documents and Settings\All Users\Documents`, avec le nom d'utilisateur `anonymous` et un mot de passe vide.  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  Le protocole FTP utilisé par la méthode `DownLoadFile` envoie les informations, y compris les mots de passe, en texte brut, et ne doit pas être utilisé pour transmettre des informations sensibles.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Network>   
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>   
 [How to: Upload a File](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)   
 [Comment : analyser des chemins d'accès](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)