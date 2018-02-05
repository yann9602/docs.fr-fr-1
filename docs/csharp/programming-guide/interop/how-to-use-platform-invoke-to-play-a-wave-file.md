---
title: "Comment : utiliser l'appel de code non managé pour lire un fichier audio (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 10c2490255565de872396a0155bb588f9d696b24
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="32968-102">Comment : utiliser l'appel de code non managé pour lire un fichier audio (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="32968-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="32968-103">L’exemple de code C# suivant explique comment utiliser des services d’appel de code non managé pour lire un fichier audio sur le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="32968-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32968-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="32968-104">Example</span></span>  
 <span data-ttu-id="32968-105">Cet exemple de code utilise `DllImport` pour importer le point d’entrée de la méthode `PlaySound` de `winmm.dll` sous la forme `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="32968-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="32968-106">L’exemple utilise un formulaire Windows Form simple avec un bouton.</span><span class="sxs-lookup"><span data-stu-id="32968-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="32968-107">En cliquant sur le bouton, vous ouvrez une boîte de dialogue <xref:System.Windows.Forms.OpenFileDialog> Windows standard qui permet d’ouvrir un fichier à lire.</span><span class="sxs-lookup"><span data-stu-id="32968-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="32968-108">Quand un fichier audio est sélectionné, il est lu à l’aide de la méthode `PlaySound()` de la méthode d’assembly winmm.DLL.</span><span class="sxs-lookup"><span data-stu-id="32968-108">When a wave file is selected, it is played by using the `PlaySound()` method of the winmm.DLL assembly method.</span></span> <span data-ttu-id="32968-109">Pour plus d’informations sur la méthode `PlaySound` de winmm.dll, consultez [Using the PlaySound function with Waveform-Audio Files](https://msdn.microsoft.com/library/aa910379.aspx) (Utilisation de la fonction PlaySound avec les fichiers de formes d’ondes audio).</span><span class="sxs-lookup"><span data-stu-id="32968-109">For more information about winmm.dll's `PlaySound` method, see [Using the PlaySound function with Waveform-Audio Files](https://msdn.microsoft.com/library/aa910379.aspx).</span></span> <span data-ttu-id="32968-110">Recherchez et sélectionnez un fichier avec une extension .wav, puis cliquez sur **Ouvrir** pour lire le fichier audio à l’aide de l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="32968-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="32968-111">Une zone de texte affiche le chemin complet du fichier sélectionné.</span><span class="sxs-lookup"><span data-stu-id="32968-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="32968-112">La boîte de dialogue **Ouvrir les fichiers** est filtrée pour afficher uniquement les fichiers avec une extension .wav au moyen des paramètres de filtre :</span><span class="sxs-lookup"><span data-stu-id="32968-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="32968-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="32968-113">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="32968-114">Pour compiler le code</span><span class="sxs-lookup"><span data-stu-id="32968-114">To compile the code</span></span>  
  
1.  <span data-ttu-id="32968-115">Créez un projet d’application Windows C# dans Visual Studio et nommez-le **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="32968-115">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="32968-116">Copiez le code ci-dessus et collez-le sur le contenu du fichier `Form1.cs`.</span><span class="sxs-lookup"><span data-stu-id="32968-116">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="32968-117">Copiez le code suivant et collez-le dans le fichier `Form1.Designer.cs`, dans la méthode `InitializeComponent()`, après tout le code existant.</span><span class="sxs-lookup"><span data-stu-id="32968-117">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  <span data-ttu-id="32968-118">Compilez, puis exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="32968-118">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="32968-119">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32968-119">.NET Framework Security</span></span>  
 <span data-ttu-id="32968-120">Pour plus d’informations, consultez [Sécurité .NET Framework](https://technet.microsoft.com/en-us/security/).</span><span class="sxs-lookup"><span data-stu-id="32968-120">For more information, see [.NET Framework Security](https://technet.microsoft.com/en-us/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32968-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32968-121">See Also</span></span>  
 [<span data-ttu-id="32968-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="32968-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="32968-123">Vue d’ensemble de l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="32968-123">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [<span data-ttu-id="32968-124">Présentation détaillée de l’appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="32968-124">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
 [<span data-ttu-id="32968-125">Marshaling de données à l’aide de l’appel de code managé</span><span class="sxs-lookup"><span data-stu-id="32968-125">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
