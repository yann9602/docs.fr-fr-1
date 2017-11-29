---
title: Error, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cd3245fd3e9e62b1b6443e9787c97808a0d179d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="error-statement"></a>Error, instruction
Simule la présence d’une erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>Composants  
 `errornumber`  
 Obligatoire. Peut être n’importe quel numéro d’erreur valide.  
  
## <a name="remarks"></a>Remarques  
 La `Error` instruction est prise en charge pour la compatibilité descendante. Dans le nouveau code, notamment lors de la création d’objets, utilisez la `Err` l’objet `Raise` méthode pour générer des erreurs d’exécution.  
  
 Si `errornumber` est défini, le `Error` instruction appelle le Gestionnaire d’erreurs après les propriétés de la `Err` objet affecté les valeurs par défaut suivantes :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|`Number`|Valeur spécifiée en tant qu’argument à `Error` instruction. Peut être n’importe quel numéro d’erreur valide.|  
|`Source`|Nom du projet Visual Basic actuel.|  
|`Description`|Expression de chaîne correspondant à la valeur de retour de la `Error` fonction spécifié `Number`, si cette chaîne existe. Si la chaîne n’existe pas, `Description` contient une chaîne de longueur nulle ( » »).|  
|`HelpFile`|Le lecteur complet, le chemin d’accès et le nom de fichier du fichier d’aide Visual Basic approprié.|  
|`HelpContext`|ID de contexte pour l’erreur correspondant à l’aide de Visual Basic approprié du fichier le `Number` propriété.|  
|`LastDLLError`|Zéro.|  
  
 Si aucun gestionnaire d’erreur existe, ou si aucune n’est activée, un message d’erreur est créé et affiché à partir de la `Err` propriétés de l’objet.  
  
> [!NOTE]
>  Certaines applications hôtes de Visual Basic ne peut pas créer des objets. Consultez la documentation de votre application hôte pour déterminer si elle peut créer des classes et des objets.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la `Error` instruction à générer l’erreur numéro 11.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Spécifications  
 **Namespace :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly :** bibliothèque Visual Basic Runtime (dans Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [On Error (instruction)](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Resume (instruction)](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Messages d’erreur](../../../visual-basic/language-reference/error-messages/index.md)
