---
title: "-baseaddress (Options du compilateur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7cd3269754f783ab8b26683f5215aa81825673e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="baseaddress-c-compiler-options"></a>/baseaddress (Options du compilateur C#)
L’option **/baseaddress** vous permet de spécifier l’adresse de base préférée à laquelle doit être chargée une DLL. Pour plus d’informations sur quand et pourquoi utiliser cette option, consultez [blog de Larry Osterman](http://go.microsoft.com/fwlink/?LinkId=107044).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
 `address`  
 Adresse de base de la DLL. Cette adresse peut être spécifiée sous forme d’un nombre décimal, hexadécimal ou octal.  
  
## <a name="remarks"></a>Remarques  
 L’adresse de base par défaut d’une DLL est définie par le Common Language Runtime (CLR) .NET Framework.  
  
 Sachez que le dernier chiffre de cette adresse sera arrondi. Par exemple, si vous spécifiez l’adresse 0x11110001, elle est arrondie à 0x11110000.  
  
 Pour terminer le processus de signature d’une DLL, utilisez SN.EXE avec l’option -R.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Cliquez sur le bouton **Avancées** .  
  
4.  Modifiez la propriété **Adresse de base de la DLL**.  
  
     Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
