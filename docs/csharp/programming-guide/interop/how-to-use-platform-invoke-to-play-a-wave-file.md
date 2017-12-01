---
title: "Comment : utiliser l'appel de code non managé pour lire un fichier audio (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d037e17ef48ebfdd5cfd860efbacf195e7b6a76d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Comment : utiliser l'appel de code non managé pour lire un fichier audio (Guide de programmation C#)
L’exemple de code C# suivant explique comment utiliser des services d’appel de code non managé pour lire un fichier audio sur le système d’exploitation Windows.  
  
## <a name="example"></a>Exemple  
 Cet exemple de code utilise `DllImport` pour importer le point d’entrée de la méthode `PlaySound` de `winmm.dll` sous la forme `Form1 PlaySound()`. L’exemple utilise un formulaire Windows Form simple avec un bouton. En cliquant sur le bouton, vous ouvrez une boîte de dialogue <xref:System.Windows.Forms.OpenFileDialog> Windows standard qui permet d’ouvrir un fichier à lire. Quand un fichier audio est sélectionné, il est lu à l’aide de la méthode `PlaySound()` de la méthode d’assembly winmm.DLL. Pour plus d’informations sur la méthode `PlaySound` de winmm.dll, consultez [Using the PlaySound function with Waveform-Audio Files](http://go.microsoft.com/fwlink/?LinkId=148553) (Utilisation de la fonction PlaySound avec les fichiers de formes d’ondes audio). Recherchez et sélectionnez un fichier avec une extension .wav, puis cliquez sur **Ouvrir** pour lire le fichier audio à l’aide de l’appel de code non managé. Une zone de texte affiche le chemin complet du fichier sélectionné.  
  
 La boîte de dialogue **Ouvrir les fichiers** est filtrée pour afficher uniquement les fichiers avec une extension .wav au moyen des paramètres de filtre :  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
### <a name="to-compile-the-code"></a>Pour compiler le code  
  
1.  Créez un projet d’application Windows C# dans Visual Studio et nommez-le **WinSound**.  
  
2.  Copiez le code ci-dessus et collez-le sur le contenu du fichier `Form1.cs`.  
  
3.  Copiez le code suivant et collez-le dans le fichier `Form1.Designer.cs`, dans la méthode `InitializeComponent()`, après tout le code existant.  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  Compilez, puis exécutez le code.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Pour plus d’informations, consultez [Sécurité .NET Framework](http://go.microsoft.com/fwlink/?LinkId=37122).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Vue d’ensemble de l’interopérabilité](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [Vue d’ensemble de l’interopérabilité](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [L’appel de plateforme plus approfondie](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [Marshaling de données à l’aide de l’appel de code managé](../../../framework/interop/marshaling-data-with-platform-invoke.md)
