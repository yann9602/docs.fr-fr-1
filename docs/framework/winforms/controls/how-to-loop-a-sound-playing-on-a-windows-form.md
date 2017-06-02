---
title: "Comment&#160;: mettre en boucle la lecture d&#39;un son dans un Windows Form | Microsoft Docs"
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
  - "lire des sons, boucle"
  - "boucles audio"
  - "SoundPlayer (classe), lire en boucle"
  - "sons, boucle"
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: mettre en boucle la lecture d&#39;un son dans un Windows Form
L'exemple de code suivant joue un son de manière répétitive.  Quand le code du gestionnaire d'événements `stopPlayingButton_Click` est exécuté, le son s'arrête.  Si aucun son n'est joué, rien ne se produit.  
  
## Exemple  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux assemblys System et System.Windows.Forms ;  
  
-   que vous remplaciez le nom de fichier `"c:\Windows\Media\chimes.wav"` par un nom de fichier valide.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], voir [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Voir également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## Programmation fiable  
 Les opérations de fichiers doivent être placées dans des blocs de gestion des exceptions appropriés.  
  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le chemin d'accès est mal formé.  Par exemple, il contient des caractères qui ne sont pas valides ou est constitué uniquement d'espaces blancs \(classe <xref:System.ArgumentException>\).  
  
-   Le chemin d'accès est en lecture seule \(classe <xref:System.IO.IOException>\).  
  
-   Le nom du chemin d'accès est `Nothing` \(classe <xref:System.ArgumentNullException>\).  
  
-   Le nom du chemin d'accès est trop long \(classe <xref:System.IO.PathTooLongException>\).  
  
-   Le chemin d'accès n'est pas valide \(classe <xref:System.IO.DirectoryNotFoundException>\).  
  
-   Le chemin d'accès n'est constitué que d'un signe deux\-points \(":"\) \(classe <xref:System.NotSupportedException>\).  
  
## Sécurité .NET Framework  
 Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu.  Par exemple, le fichier Form1.vb peut ne pas être un fichier source Visual Basic.  Vérifiez toutes les entrées avant d'utiliser les données dans votre application.  
  
## Voir aussi  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>   
 [Comment : lire un son à partir d'un Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)   
 [Vue d'ensemble de la classe SoundPlayer](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)