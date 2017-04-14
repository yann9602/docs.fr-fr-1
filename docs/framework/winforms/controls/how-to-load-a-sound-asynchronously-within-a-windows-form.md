---
title: "Comment&#160;: charger un son de fa&#231;on asynchrone dans un Windows Form | Microsoft Docs"
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
  - "SoundPlayer (classe), charger les sons de manière asynchrone"
  - "sons, le chargement sur des threads séparés"
  - "threads (Windows Forms), des sons"
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: charger un son de fa&#231;on asynchrone dans un Windows Form
L'exemple de code suivant charge un son de façon asynchrone à partir d'une URL et le lit sur un nouveau thread.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux assemblys System et System.Windows.Forms ;  
  
-   que vous remplaciez le nom de fichier `"http://www.tailspintoys.com/sounds/stop.wav"` par un nom de fichier valide.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [de ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un complet Windows Forms Code exemple à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les opérations de fichiers doivent être placées dans des blocs de gestion des exceptions appropriés.  
  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le chemin d’accès est mal formé. Par exemple, il contient des caractères qui ne sont pas valides ou est uniquement un espace blanc (<xref:System.ArgumentException> classe).  
  
-   Le chemin d’accès est en lecture seule (<xref:System.IO.IOException> classe).  
  
-   Le nom de chemin d’accès est `Nothing` (<xref:System.ArgumentNullException> classe).  
  
-   Le nom de chemin d’accès est trop long (<xref:System.IO.PathTooLongException> classe).  
  
-   Le chemin d’accès n’est pas valide (<xref:System.IO.DirectoryNotFoundException> classe).  
  
-   Le chemin d’accès n'est qu’un signe deux-points « : » (<xref:System.NotSupportedException> classe).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu. Par exemple, le fichier `Form1.vb` peut ne pas être un fichier source Visual Basic. Vérifiez toutes les entrées avant d'utiliser les données dans votre application.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>   
 <xref:System.Media.SoundPlayer.LoadCompleted>   
 <xref:System.Media.SoundPlayer.Play%2A>   
 [Comment : lire un son à partir d’un Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)