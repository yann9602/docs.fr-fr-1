---
title: "Guide pratique pour émettre un signal sonore à partir d'un Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], beep
- Windows Forms, sounds
- sounds [Windows Forms], playing
- forms [Windows Forms], sounds
- examples [Windows Forms], sounds
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e214b368b65797100722cb41ad6a77ecd16424de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="b7397-102">Guide pratique pour émettre un signal sonore à partir d'un Windows Form</span><span class="sxs-lookup"><span data-stu-id="b7397-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="b7397-103">Cet exemple émet un signal sonore à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b7397-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7397-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7397-104">Example</span></span>  
  
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
>  <span data-ttu-id="b7397-105">Le son exécuté dans l’exemple de code c# est déterminé par le <xref:System.Media.SystemSounds.Beep%2A> paramètre de son système.</span><span class="sxs-lookup"><span data-stu-id="b7397-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="b7397-106">Pour plus d'informations, consultez <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="b7397-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b7397-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b7397-107">Compiling the Code</span></span>  
 <span data-ttu-id="b7397-108">Pour c#, cet exemple requiert une référence à la <xref:System.Media?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="b7397-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7397-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7397-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="b7397-110">Guide pratique pour émettre un son système à partir d’un Windows Form</span><span class="sxs-lookup"><span data-stu-id="b7397-110">How to: Play a System Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 [<span data-ttu-id="b7397-111">Guide pratique pour lire un son à partir d’un Windows Form</span><span class="sxs-lookup"><span data-stu-id="b7397-111">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
