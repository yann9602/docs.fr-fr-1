---
title: "Comment&#160;: cr&#233;er un fichier ou un dossier (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "créer des fichiers (C#)"
  - "créer des dossiers (C#)"
  - "fichiers (C#)"
  - "dossiers (C#)"
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: cr&#233;er un fichier ou un dossier (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous pouvez créer par programmation un dossier sur votre ordinateur, créer un sous\-dossier, créer un fichier dans le sous\-dossier, puis écrire les données dans le fichier.  
  
## Exemple  
 [!code-cs[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]  
  
 Si le dossier existe déjà, <xref:System.IO.Directory.CreateDirectory%2A> est sans effet et aucune exception n'est levée.  Toutefois, <xref:System.IO.File.Create%2A?displayProperty=fullName> remplace un fichier existant par un nouveau fichier.  L'exemple utilise une instruction `if`\-`else` pour empêcher le remplacement d'un fichier existant.  
  
 En effectuant les modifications suivantes dans l'exemple, vous pouvez spécifier différentes issues suivant qu'un fichier d'un certain nom existe déjà.  Si ce fichier n'existe pas, le code en crée un.  Si ce fichier existe, le code y ajoute des données.  
  
-   Spécifiez un nom de fichier non aléatoire.  
  
    ```c#  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
  
    ```  
  
-   Remplacez l'instruction `if`\-`else` par l'instruction `using` dans le code suivant.  
  
    ```c#  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
  
    ```  
  
 Exécutez plusieurs fois l'exemple pour vérifier que les données sont ajoutées au fichier à chaque fois.  
  
 Pour d'autres valeurs `FileMode` que vous pouvez essayer, consultez <xref:System.IO.FileMode>.  
  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le nom de dossier est incorrect.  Il contient par exemple des caractères non valides ou se compose uniquement d'un espace blanc \(classe <xref:System.ArgumentException>\).  Utilisez la classe <xref:System.IO.Path> pour créer des noms de chemin d'accès valides.  
  
-   Le dossier parent du dossier à créer est en lecture seule \(<xref:System.IO.IOException>, classe\).  
  
-   Le nom du dossier est `null` \(classe <xref:System.ArgumentNullException>\).  
  
-   Le nom du dossier est trop long \(classe <xref:System.IO.PathTooLongException>\).  
  
-   Le nom du dossier se compose uniquement du signe deux\-points ":" \(classe <xref:System.IO.PathTooLongException>\).  
  
## Sécurité .NET Framework  
 Une instance de la classe <xref:System.Security.SecurityException> peut être levée dans des situations où le niveau de confiance n'est pas total.  
  
 Si vous n'êtes pas autorisé à créer le dossier, l'exemple lève une instance de la classe <xref:System.UnauthorizedAccessException>.  
  
## Voir aussi  
 <xref:System.IO?displayProperty=fullName>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Système de fichiers et Registre](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)