---
title: "Comment&#160;: lire un son incorpor&#233; dans une ressource &#224; partir d&#39;un Windows Form | Microsoft Docs"
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
  - "lecture des sons, des ressources"
  - "ressources (Windows Forms), lire des sons"
  - "lire des sons, des ressources"
  - "SoundPlayer (classe), lire des sons à partir des ressources"
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: lire un son incorpor&#233; dans une ressource &#224; partir d&#39;un Windows Form
Vous pouvez utiliser la <xref:System.Media.SoundPlayer> classe pour lire un son à partir d’une ressource incorporée.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
 L’importation de la <xref:System.Media?displayProperty=fullName> espace de noms.  
  
 En tant que ressource incorporée dans votre projet, y compris le fichier audio.  
  
 En remplaçant «<>\>» avec le nom de l’assembly dans lequel le fichier audio est incorporé. N’incluez pas le suffixe « .dll ».  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Media.SoundPlayer>   
 [Comment : lire un son à partir d’un Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)   
 [Comment : mettre en boucle un son sur un Windows Form](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)