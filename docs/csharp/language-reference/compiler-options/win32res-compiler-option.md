---
title: "/win32res (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/win32res"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "win32res compiler option"
  - "/win32res compiler option [C#]"
  - "-win32res compiler option [C#]"
  - "win32res compiler option [C#]"
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# /win32res (C# Compiler Options)
L'option **\/win32res** insère une ressource Win32 dans le fichier de sortie.  
  
## Syntaxe  
  
```  
/win32res:filename  
```  
  
## Arguments  
 `filename`  
 Nom du fichier de ressources que vous voulez ajouter à votre fichier de sortie.  
  
## Notes  
 Un fichier de ressources Win32 peut être créé à l'aide du [compilateur de ressources](http://go.microsoft.com/fwlink/?LinkId=148370).  Le compilateur de ressources est appelé lorsque vous compilez un programme Visual C\+\+ ; un fichier .res est alors créé à partir du fichier .rc.  
  
 Une ressource Win32 peut comprendre des informations sur la version ou le fichier bitmap \(icône\) qui permettent d'identifier votre application dans l'Explorateur Windows.  Si vous ne spécifiez pas l'option **\/win32res**, le compilateur génère des informations de version en fonction de la version de l'assembly.  
  
 Consultez [\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) pour référencer ou [\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) pour attacher un fichier de ressources .NET Framework.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Application**.  
  
3.  Cliquez sur le bouton **Fichier de ressources** et choisissez un fichier dans la zone de liste déroulante.  
  
## Exemple  
 Compilez `in.cs` et attachez le fichier de ressources Win32 `rf.res` afin d'obtenir le fichier `in.exe` :  
  
```  
csc /win32res:rf.res in.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)