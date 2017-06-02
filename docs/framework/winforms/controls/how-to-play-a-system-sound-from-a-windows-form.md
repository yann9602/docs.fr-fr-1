---
title: "Comment&#160;: lire un son syst&#232;me &#224; partir d&#39;un Windows Form | Microsoft Docs"
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
  - "lecture des sons, des événements de système"
  - "lire des sons, Windows Forms"
  - "sons système, lire à partir des Windows Forms"
  - "lire des sons, système"
  - "SoundPlayer (classe), les sons système"
  - "lecture des sons"
  - "exemples (Windows Forms), des sons"
ms.assetid: afb206ff-4824-4804-a8d4-185bf5ad8e7c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: lire un son syst&#232;me &#224; partir d&#39;un Windows Form
Le code suivant joué par exemple le `Exclamation` son système en cours d’exécution. Pour plus d’informations sur les sons système, consultez la page <xref:System.Media.SystemSounds>.  
  
## <a name="example"></a>Exemple  
  
```vb  
Public Sub PlayExclamation()  
    SystemSounds.Exclamation.Play()  
End Sub  
  
```  
  
```csharp  
public void playExclamation()  
{  
    SystemSounds.Exclamation.Play();  
}  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Une référence à la <xref:System.Media?displayProperty=fullName> espace de noms.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Media.SoundPlayer>   
 <xref:System.Media.SystemSounds>   
 [Comment : émettre un signal sonore à partir d’un Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)   
 [Comment : lire un son à partir d’un Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)