---
title: "Comment&#160;: &#233;mettre un signal sonore &#224; partir d&#39;un Windows Form | Microsoft Docs"
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
  - "sons, signal sonore"
  - "Windows Forms, des sons"
  - "lecture des sons"
  - "formulaires, des sons"
  - "exemples (Windows Forms), des sons"
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: &#233;mettre un signal sonore &#224; partir d&#39;un Windows Form
Cet exemple lit un signal sonore au moment de l’exécution.  
  
## <a name="example"></a>Exemple  
  
```vb  
Public Sub OnePing()  
    Beep()  
End Sub  
```  
  
```csharp  
public void onePing()  
{  
    SystemSounds.Beep.Play();  
}  
```  
  
> [!NOTE]
>  Le son exécuté dans l’exemple de code c# est déterminé par le <xref:System.Media.SystemSounds.Beep%2A> paramètre de son système. Pour plus d’informations, consultez <xref:System.Media.SystemSounds>.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour c#, cet exemple requiert une référence à la <xref:System.Media?displayProperty=fullName> espace de noms.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>   
 <xref:System.Media.SoundPlayer>   
 [Comment : lire un son système à partir d’un Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)   
 [Comment : lire un son à partir d’un Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)