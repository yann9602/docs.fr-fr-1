---
title: Lecture de sons (Visual Basic)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a15efff54bd54fdaced6c741cd6acf5c8b544cdd
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="8e810-102">Lecture de sons (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e810-102">Playing Sounds (Visual Basic)</span></span>
<span data-ttu-id="8e810-103">L’objet `My.Computer.Audio` fournit des méthodes permettant de lire des sons.</span><span class="sxs-lookup"><span data-stu-id="8e810-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="8e810-104">Lecture de sons</span><span class="sxs-lookup"><span data-stu-id="8e810-104">Playing Sounds</span></span>  
 <span data-ttu-id="8e810-105">Avec la lecture en arrière-plan, l’application peut exécuter du code pendant la lecture d’un son.</span><span class="sxs-lookup"><span data-stu-id="8e810-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="8e810-106">La méthode `My.Computer.Audio.Play` permet à l’application de lire un seul fond sonore à la fois. Quand elle lit un nouveau fond sonore, l’application arrête la lecture du fond sonore précédent.</span><span class="sxs-lookup"><span data-stu-id="8e810-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="8e810-107">L’application peut également lire un son et attendre qu’il s’arrête.</span><span class="sxs-lookup"><span data-stu-id="8e810-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="8e810-108">Dans l’exemple suivant, la méthode `My.Computer.Audio.Play` lit un son.</span><span class="sxs-lookup"><span data-stu-id="8e810-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="8e810-109">Quand `AudioPlayMode.WaitToComplete` est spécifié, `My.Computer.Audio.Play` attend que le son s’arrête pour que l’exécution du code appelant continue.</span><span class="sxs-lookup"><span data-stu-id="8e810-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="8e810-110">Si vous utilisez cet exemple, assurez-vous que le nom de fichier fait référence à un fichier son .wav enregistré sur votre ordinateur</span><span class="sxs-lookup"><span data-stu-id="8e810-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 <span data-ttu-id="8e810-111">[!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8e810-111">[!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]</span></span>  
  
 <span data-ttu-id="8e810-112">Dans l’exemple suivant, la méthode `My.Computer.Audio.Play` lit un son.</span><span class="sxs-lookup"><span data-stu-id="8e810-112">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="8e810-113">Si vous utilisez cet exemple, assurez-vous que les ressources d’application incluent un fichier son .wav nommé Waterfall.</span><span class="sxs-lookup"><span data-stu-id="8e810-113">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 <span data-ttu-id="8e810-114">[!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8e810-114">[!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]</span></span>  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="8e810-115">Lecture de sons en boucle</span><span class="sxs-lookup"><span data-stu-id="8e810-115">Playing Looping Sounds</span></span>  
 <span data-ttu-id="8e810-116">Dans l’exemple suivant, la méthode `My.Computer.Audio.Play` lit le son spécifié en arrière-plan quand `PlayMode.BackgroundLoop` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="8e810-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="8e810-117">Si vous utilisez cet exemple, assurez-vous que le nom de fichier fait référence à un fichier son .wav enregistré sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8e810-117">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 <span data-ttu-id="8e810-118">[!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="8e810-118">[!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]</span></span>  
  
 <span data-ttu-id="8e810-119">Dans l’exemple suivant, la méthode `My.Computer.Audio.Play` lit le son spécifié en arrière-plan quand `PlayMode.BackgroundLoop` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="8e810-119">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="8e810-120">Si vous utilisez cet exemple, assurez-vous que les ressources d’application incluent un fichier son .wav nommé Waterfall.</span><span class="sxs-lookup"><span data-stu-id="8e810-120">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 <span data-ttu-id="8e810-121">[!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="8e810-121">[!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]</span></span>  
  
 <span data-ttu-id="8e810-122">L’exemple de code précédent est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8e810-122">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="8e810-123">Dans le sélecteur d’extraits de code, il se trouve dans **Applications Windows Forms > Son**.</span><span class="sxs-lookup"><span data-stu-id="8e810-123">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="8e810-124">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="8e810-124">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="8e810-125">En général, quand une application lit un son en boucle, elle doit finir par l’arrêter.</span><span class="sxs-lookup"><span data-stu-id="8e810-125">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="8e810-126">Arrêt de la lecture de sons en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="8e810-126">Stopping the Playing of Sounds in the Background</span></span>  
 <span data-ttu-id="8e810-127">Utilisez la méthode `My.Computer.Audio.Stop` pour arrêter la lecture en arrière-plan ou en boucle d’un son dans l’application.</span><span class="sxs-lookup"><span data-stu-id="8e810-127">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="8e810-128">En général, quand une application lit un son en boucle, elle doit l’arrêter à un certain point.</span><span class="sxs-lookup"><span data-stu-id="8e810-128">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="8e810-129">L’exemple suivant arrête un son qui est lu en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="8e810-129">The following example stops a sound that is playing in the background.</span></span>  
  
 <span data-ttu-id="8e810-130">[!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="8e810-130">[!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]</span></span>  
  
 <span data-ttu-id="8e810-131">L’exemple de code précédent est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8e810-131">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="8e810-132">Dans le sélecteur d’extraits de code, il se trouve dans **Applications Windows Forms > Son**.</span><span class="sxs-lookup"><span data-stu-id="8e810-132">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="8e810-133">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="8e810-133">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="8e810-134">Lecture de sons système</span><span class="sxs-lookup"><span data-stu-id="8e810-134">Playing System Sounds</span></span>  
 <span data-ttu-id="8e810-135">Utilisez la méthode `My.Computer.Audio.PlaySystemSound` pour lire le son système spécifié.</span><span class="sxs-lookup"><span data-stu-id="8e810-135">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="8e810-136">La méthode `My.Computer.Audio.PlaySystemSound` prend comme paramètre l’un des membres partagés de la classe <xref:System.Media.SystemSound>.</span><span class="sxs-lookup"><span data-stu-id="8e810-136">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="8e810-137">Le son système <xref:System.Media.SystemSounds.Asterisk%2A> indique généralement des erreurs.</span><span class="sxs-lookup"><span data-stu-id="8e810-137">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="8e810-138">L’exemple suivant utilise la méthode `My.Computer.Audio.PlaySystemSound` pour lire un son système.</span><span class="sxs-lookup"><span data-stu-id="8e810-138">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 <span data-ttu-id="8e810-139">[!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="8e810-139">[!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e810-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e810-140">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Audio>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>   
 <xref:Microsoft.VisualBasic.AudioPlayMode>

