---
title: "Comment&#160;: utiliser l&#39;appel de code non manag&#233; pour lire un fichier audio (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "fichiers .wav"
  - "interopérabilité (C#), lire les fichiers .wav à l'aide de pinvoke"
  - "appel de code non managé, fichiers audio"
  - "fichiers .wav"
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: utiliser l&#39;appel de code non manag&#233; pour lire un fichier audio (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'exemple de code C\# suivant illustre comment utiliser les services d'appel de code managé pour lire un fichier son .wav sur le système d'exploitation Windows.  
  
## Exemple  
 Cet exemple de code utilise `DllImport` pour importer le point d'entrée de la méthode `PlaySound` de `winmm.dll` comme `Form1 PlaySound()`.  L'exemple a un simple Windows Form doté d'un bouton.  Cliquez sur le bouton pour ouvrir une boîte de dialogue <xref:System.Windows.Forms.OpenFileDialog> Windows standard et ouvrir le fichier que vous souhaitez lire.  Lorsqu'un fichier .wav est sélectionné, il est lu à l'aide de la méthode `PlaySound()` de la méthode d'assembly winmm.DLL.  Pour plus d'informations sur la méthode `PlaySound` de winmm.dll, consultez [Utilisation de la fonction PlaySound avec les fichiers audio Waveform \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=148553) Parcourez et sélectionnez un fichier doté d'une extension .wav, puis cliquez sur **Ouvrir** pour lire le fichier .wav à l'aide de l'appel de code non managé.  Une zone de texte affiche le chemin d'accès complet du fichier sélectionné.  
  
 La boîte de dialogue **Fichiers ouverts** utilise les paramètres de filtre suivants pour afficher uniquement les fichiers dotés d'une extension .wav :  
  
 [!code-cs[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-cs[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## Compilation du code  
  
### Pour compiler le code  
  
1.  Créez un nouveau projet d'application Windows C\# dans Visual Studio et nommez\-le WinSound.  
  
2.  Copiez le code précité et collez\-le sur le contenu du fichier `Form1.cs`.  
  
3.  Copiez le code suivant et collez\-le dans le fichier `Form1.Designer.cs`, dans la méthode `InitializeComponent()`, après tout code existant.  
  
     [!code-cs[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  Compilez et exécutez le code.  
  
## Sécurité .NET Framework  
 Pour plus d'informations, consultez [.NET Framework Security](http://go.microsoft.com/fwlink/?LinkId=37122).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Vue d'ensemble de l'interopérabilité](../../../csharp/programming-guide/interop/interoperability-overview.md)   
 [Vue d'ensemble de l'interopérabilité](../../../csharp/programming-guide/interop/interoperability-overview.md)   
 [A Closer Look at Platform Invoke](http://msdn.microsoft.com/fr-fr/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)   
 [Marshaling Data with Platform Invoke](../Topic/Marshaling%20Data%20with%20Platform%20Invoke.md)