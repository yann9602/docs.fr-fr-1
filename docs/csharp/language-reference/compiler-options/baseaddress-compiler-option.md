---
title: "-baseaddress (Options du compilateur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /dllbase
dev_langs:
- CSharp
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: 18
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
ms.openlocfilehash: 91193ae794957b5045a225614d6322e86d18d459
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="baseaddress-c-compiler-options"></a>/baseaddress (Options du compilateur C#)
L’option **/baseaddress** vous permet de spécifier l’adresse de base préférée à laquelle doit être chargée une DLL. Pour plus d’informations sur le moment et la raison de l’utilisation de cette option, consultez [Amélioration du temps de démarrage des applications](http://go.microsoft.com/fwlink/?LinkId=107043) et [journal web de Larry Osterman](http://go.microsoft.com/fwlink/?LinkId=107044).  
  
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
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=fullName>   
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)

