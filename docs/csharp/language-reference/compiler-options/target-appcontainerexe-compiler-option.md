---
title: "-target:appcontainerexe (Options du compilateur C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 168771506692308bc9b031df5c059e58e8d190b1
ms.lasthandoff: 03/13/2017

---
# <a name="targetappcontainerexe-c-compiler-options"></a>/target:appcontainerexe (Options du compilateur C#)
Si vous utilisez l’option du compilateur **/target:appcontainerexe**, le compilateur crée un fichier exécutable Windows (.exe) qui doit être exécuté dans un conteneur d’application. Cette option est équivalente à [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md), mais elle est destinée aux applications [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/target:appcontainerexe  
```  
  
## <a name="remarks"></a>Remarques  
 Pour exiger que l’application s’exécute dans un conteneur d’application, cette option définit un bit dans le fichier [Portable Executable](http://go.microsoft.com/fwlink/p/?LinkId=236960) (PE). Lorsque ce bit est défini, une erreur se produit si la méthode CreateProcess tente de lancer l'exécutable en dehors d'un conteneur d'application.  
  
 À moins que vous utilisiez l’option [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), le fichier de sortie prend le nom du fichier d’entrée qui contient la méthode [Main](../../../csharp/programming-guide/main-and-command-args/index.md).  
  
 Lorsque vous spécifiez cette option à une invite de commandes, tous les fichiers jusqu’à l’option **/out** ou **/target** suivante sont utilisés pour créer le fichier exécutable.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Pour définir cette option du compilateur dans l'IDE  
  
1.  Dans l’**Explorateur de solutions**, ouvrez le menu contextuel de votre projet et choisissez **Propriétés**.  
  
2.  Sous l’onglet **Application**, dans la liste **Type de sortie**, choisissez **Application Windows Store**.  
  
     Cette option est disponible uniquement pour les modèles d'applications [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)].  
  
 Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemple  
 La commande suivante compile `filename.cs` dans un fichier exécutable Windows qui peut être exécuté uniquement dans un conteneur d'application.  
  
```  
csc /target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Voir aussi  
 [target (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [/target:winexe (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)   
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)
