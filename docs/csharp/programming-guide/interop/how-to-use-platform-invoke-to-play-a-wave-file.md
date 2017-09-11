---
title: "Comment : utiliser l'appel de code non managé pour lire un fichier audio (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
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
ms.openlocfilehash: 001236392d2b3d3c70dbd0faf2a899929dfe8625
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="fa061-102">Comment : utiliser l'appel de code non managé pour lire un fichier audio (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="fa061-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="fa061-103">L’exemple de code C# suivant explique comment utiliser des services d’appel de code non managé pour lire un fichier audio sur le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="fa061-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa061-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="fa061-104">Example</span></span>  
 <span data-ttu-id="fa061-105">Cet exemple de code utilise `DllImport` pour importer le point d’entrée de la méthode `PlaySound` de `winmm.dll` sous la forme `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="fa061-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="fa061-106">L’exemple utilise un formulaire Windows Form simple avec un bouton.</span><span class="sxs-lookup"><span data-stu-id="fa061-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="fa061-107">En cliquant sur le bouton, vous ouvrez une boîte de dialogue <xref:System.Windows.Forms.OpenFileDialog> Windows standard qui permet d’ouvrir un fichier à lire.</span><span class="sxs-lookup"><span data-stu-id="fa061-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="fa061-108">Quand un fichier audio est sélectionné, il est lu à l’aide de la méthode `PlaySound()` de la méthode d’assembly winmm.DLL.</span><span class="sxs-lookup"><span data-stu-id="fa061-108">When a wave file is selected, it is played by using the `PlaySound()` method of the winmm.DLL assembly method.</span></span> <span data-ttu-id="fa061-109">Pour plus d’informations sur la méthode `PlaySound` de winmm.dll, consultez [Using the PlaySound function with Waveform-Audio Files](http://go.microsoft.com/fwlink/?LinkId=148553) (Utilisation de la fonction PlaySound avec les fichiers de formes d’ondes audio).</span><span class="sxs-lookup"><span data-stu-id="fa061-109">For more information about winmm.dll's `PlaySound` method, see [Using the PlaySound function with Waveform-Audio Files](http://go.microsoft.com/fwlink/?LinkId=148553).</span></span> <span data-ttu-id="fa061-110">Recherchez et sélectionnez un fichier avec une extension .wav, puis cliquez sur **Ouvrir** pour lire le fichier audio à l’aide de l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="fa061-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="fa061-111">Une zone de texte affiche le chemin complet du fichier sélectionné.</span><span class="sxs-lookup"><span data-stu-id="fa061-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="fa061-112">La boîte de dialogue **Ouvrir les fichiers** est filtrée pour afficher uniquement les fichiers avec une extension .wav au moyen des paramètres de filtre :</span><span class="sxs-lookup"><span data-stu-id="fa061-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 <span data-ttu-id="fa061-113">[!code-cs[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="fa061-113">[!code-cs[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]</span></span>  
  
 <span data-ttu-id="fa061-114">[!code-cs[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="fa061-114">[!code-cs[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fa061-115">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="fa061-115">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="fa061-116">Pour compiler le code</span><span class="sxs-lookup"><span data-stu-id="fa061-116">To compile the code</span></span>  
  
1.  <span data-ttu-id="fa061-117">Créez un projet d’application Windows C# dans Visual Studio et nommez-le **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="fa061-117">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="fa061-118">Copiez le code ci-dessus et collez-le sur le contenu du fichier `Form1.cs`.</span><span class="sxs-lookup"><span data-stu-id="fa061-118">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="fa061-119">Copiez le code suivant et collez-le dans le fichier `Form1.Designer.cs`, dans la méthode `InitializeComponent()`, après tout le code existant.</span><span class="sxs-lookup"><span data-stu-id="fa061-119">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     <span data-ttu-id="fa061-120">[!code-cs[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="fa061-120">[!code-cs[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]</span></span>  
  
4.  <span data-ttu-id="fa061-121">Compilez, puis exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="fa061-121">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fa061-122">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fa061-122">.NET Framework Security</span></span>  
 <span data-ttu-id="fa061-123">Pour plus d’informations, consultez [Sécurité .NET Framework](http://go.microsoft.com/fwlink/?LinkId=37122).</span><span class="sxs-lookup"><span data-stu-id="fa061-123">For more information, see [.NET Framework Security](http://go.microsoft.com/fwlink/?LinkId=37122).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa061-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa061-124">See Also</span></span>  
 <span data-ttu-id="fa061-125">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="fa061-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="fa061-126">[Vue d’ensemble de l’interopérabilité](../../../csharp/programming-guide/interop/interoperability-overview.md) </span><span class="sxs-lookup"><span data-stu-id="fa061-126">[Interoperability Overview](../../../csharp/programming-guide/interop/interoperability-overview.md) </span></span>  
 <span data-ttu-id="fa061-127">[Vue d’ensemble de l’interopérabilité](../../../csharp/programming-guide/interop/interoperability-overview.md) </span><span class="sxs-lookup"><span data-stu-id="fa061-127">[Interoperability Overview](../../../csharp/programming-guide/interop/interoperability-overview.md) </span></span>  
 <span data-ttu-id="fa061-128">[Présentation détaillée de l'appel de code non managé](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243) </span><span class="sxs-lookup"><span data-stu-id="fa061-128">[A Closer Look at Platform Invoke](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243) </span></span>  
 [<span data-ttu-id="fa061-129">Marshaling de données à l’aide de l’appel de code managé</span><span class="sxs-lookup"><span data-stu-id="fa061-129">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)

