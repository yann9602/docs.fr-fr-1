---
title: "Comment&#160;: lire un son &#224; partir d&#39;un Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "lire des sons, Windows Forms"
  - "lecture des sons"
  - "SoundPlayer (classe)"
  - "sons"
  - "My.Computer.Audio (objet), lire des sons"
  - "exemples (Windows Forms), des sons"
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: lire un son &#224; partir d&#39;un Windows Form
Cet exemple lit un son à un chemin d’accès donné au moment de l’exécution.  
  
## <a name="example"></a>Exemple  
  
```vb  
Sub PlaySimpleSound()  
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")  
End Sub  
```  
  
```csharp  
private void playSimpleSound()  
{  
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");  
    simpleSound.Play();  
}  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   que vous remplaciez le nom de fichier `"c:\Windows\Media\chimes.wav"` par un nom de fichier valide.  
  
-   (C#) Une référence à la <xref:System.Media?displayProperty=fullName> espace de noms.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Opérations sur les fichiers doivent être placées dans des blocs de gestion structurée des exceptions appropriée.  
  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le chemin d’accès est mal formé. Par exemple, il contient des caractères non valides ou est uniquement un espace blanc (<xref:System.ArgumentException> classe).  
  
-   Le chemin d’accès est en lecture seule (<xref:System.IO.IOException> classe).  
  
-   Le nom de chemin d’accès est `null` (<xref:System.ArgumentNullException> classe).  
  
-   Le nom de chemin d’accès est trop long (<xref:System.IO.PathTooLongException> classe).  
  
-   Le chemin d’accès n’est pas valide (<xref:System.IO.DirectoryNotFoundException> classe).  
  
-   Le chemin d’accès est uniquement un signe deux-points, « : » (<xref:System.NotSupportedException> classe).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu. Par exemple, le fichier `Form1.vb` peut ne pas être un fichier source Visual Basic. Vérifiez toutes les entrées avant d'utiliser les données dans votre application.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Media.SoundPlayer>   
 [Comment : charger un son de façon asynchrone dans un Windows Form](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)   
 