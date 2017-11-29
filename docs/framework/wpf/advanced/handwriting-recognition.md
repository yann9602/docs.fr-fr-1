---
title: "Reconnaissance d'écriture manuscrite"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f8a202d4698c968a91a3d930138290cedfe3a83b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="handwriting-recognition"></a><span data-ttu-id="63071-102">Reconnaissance d'écriture manuscrite</span><span class="sxs-lookup"><span data-stu-id="63071-102">Handwriting Recognition</span></span>
<span data-ttu-id="63071-103">Cette section présente les notions de base de la reconnaissance relative à l’encre numérique dans la plateforme WPF.</span><span class="sxs-lookup"><span data-stu-id="63071-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="63071-104">Solutions de reconnaissance</span><span class="sxs-lookup"><span data-stu-id="63071-104">Recognition Solutions</span></span>  
 <span data-ttu-id="63071-105">L’exemple suivant montre comment reconnaître de l’encre à l’aide de la classe [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx).</span><span class="sxs-lookup"><span data-stu-id="63071-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63071-106">Cet exemple nécessite que les modules de reconnaissance d’écriture manuscrite soient installés sur le système.</span><span class="sxs-lookup"><span data-stu-id="63071-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="63071-107">Créez un projet d’application WPF dans Visual Studio, intitulé **InkRecognition**.</span><span class="sxs-lookup"><span data-stu-id="63071-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="63071-108">Remplacez le contenu du fichier Window1.xaml par le code XAML suivant.</span><span class="sxs-lookup"><span data-stu-id="63071-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="63071-109">Ce code restitue l’interface utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="63071-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="63071-110">Ajoutez une référence à l’assembly Microsoft Annotations, Microsoft.Ink.dll, qui se trouve dans \Program Files\Common Files\Microsoft Shared\Ink.</span><span class="sxs-lookup"><span data-stu-id="63071-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="63071-111">Remplacez le contenu du fichier code-behind par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="63071-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="63071-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63071-112">See Also</span></span>  
 <span data-ttu-id="63071-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span><span class="sxs-lookup"><span data-stu-id="63071-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span></span>
