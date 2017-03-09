---
title: "/win32icon (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/win32icon"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "win32icon compiler option [C#]"
  - "/win32icon compiler option [C#]"
  - "-win32icon compiler option [C#]"
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# /win32icon (C# Compiler Options)
L'option **\/win32icon** insère un fichier .ico dans le fichier de sortie, ce qui donne à celui\-ci l'apparence voulue dans l'Explorateur Windows.  
  
## Syntaxe  
  
```  
/win32icon:filename  
```  
  
## Arguments  
 `filename`  
 Fichier .ico que vous voulez ajouter à votre fichier de sortie.  
  
## Notes  
 Un fichier de .ico peut être créé avec [Compilateur de ressources](http://go.microsoft.com/fwlink/?LinkId=148370).  Le compilateur de ressources est appelé lors de la compilation d'un programme Visual C\+\+ ; un fichier .ico est alors créé à partir du fichier .rc.  
  
 Consultez [\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) pour référencer ou [\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) pour attacher un fichier de ressources .NET Framework.  Consultez [\/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) pour importer un fichier .res.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Application**.  
  
3.  Modifiez la propriété **Icône d'application**.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.  
  
## Exemple  
 Compilez `in.cs` et incorporez un fichier .ico `rf.ico` afin de générer le fichier `in.exe` :  
  
```  
csc /win32icon:rf.ico in.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)