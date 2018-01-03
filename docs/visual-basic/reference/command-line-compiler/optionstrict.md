---
title: /optionstrict
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 692681b21c243432ec8e7160bcc1eaa4e718d64d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="optionstrict"></a>/optionstrict
Applique une sémantique de type stricte pour restreindre les conversions de types implicites.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Facultatif. Le `/optionstrict+` option restreint les conversions de types implicites. La valeur par défaut de cette option est `/optionstrict-`. Le `/optionstrict+` option est identique à `/optionstrict`. Vous pouvez utiliser à la fois pour la sémantique de type permissive.  
  
 `custom`  
 Obligatoire. Avertir lors de la syntaxe de langue stricte n’est pas respectée.  
  
## <a name="remarks"></a>Notes  
 Lorsque `/optionstrict+` est activée, seules les conversions étendues peuvent être effectuées implicitement. Implicite conversions restrictives lors des conversions de types, tels que l’attribution un `Decimal` type d’objet à un objet de type entier, sont signalées comme des erreurs.  
  
 Pour générer des avertissements pour les conversions restrictives implicites, utilisez `/optionstrict:custom`. Utilisez `/nowarn:numberlist` à ignorer certains avertissements et `/warnaserror:numberlist` à traiter certains avertissements comme des erreurs.  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a>Pour définir /optionstrict dans l’IDE de Visual Studio  
  
1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés.**   
  
2.  Cliquez sur l’onglet **Compiler**.  
  
3.  Modifiez la valeur dans la **Option Strict** boîte.  
  
### <a name="to-set-optionstrict-programmatically"></a>Pour définir /optionstrict par programme  
  
-   Consultez [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `Test.vb` à l’aide de la sémantique de type stricte.  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [/warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
