---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dab9115c31e538bd28583b9f0591ae0c9611e2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Spécifie qu’une propriété peut être écrite, mais pas en lecture.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="rules"></a>Règles  
 **Contexte de déclaration.** Vous pouvez utiliser `WriteOnly` seulement au niveau du module. Cela signifie que le contexte de déclaration pour une `WriteOnly` propriété doit être une classe, une structure ou un module et ne peut pas être un fichier source, un espace de noms ou une procédure.  
  
 Vous pouvez déclarer une propriété comme `WriteOnly`, mais pas une variable.  
  
## <a name="when-to-use-writeonly"></a>Quand utiliser WriteOnly  
 Parfois vous souhaitez que le code de consommation pour pouvoir définir une valeur, mais pas découvrir ce qu’il est. Par exemple, les données sensibles, comme un numéro d’enregistrement sociaux ou un mot de passe doivent être protégé contre tout accès par tout composant qui définissait pas. Dans ce cas, vous pouvez utiliser un `WriteOnly` pour définir la valeur de propriété.  
  
> [!IMPORTANT]
>  Lorsque vous définissez et utilisez un `WriteOnly` propriété, tenez compte des mesures de protection supplémentaires suivantes :  
  
-   **Substitution.** Si la propriété est un membre d’une classe, autoriser sa valeur par défaut à [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)et ne la déclarez pas `Overridable` ou `MustOverride`. Cela empêche une classe dérivée qui effectue un droit d’accès via un remplacement.  
  
-   **Niveau d’accès.** Si vous stockez des données sensibles de la propriété dans une ou plusieurs variables, déclarez-les [privée](../../../visual-basic/language-reference/modifiers/private.md) afin qu’aucun autre code ne peut y accéder.  
  
-   **Chiffrement.** Stocker toutes les données sensibles sous forme chiffrée plutôt qu’en texte brut. Si un code malveillant accède une certaine manière à cette zone de mémoire, il est plus difficile d’utiliser des données. Le chiffrement est également utile s’il est nécessaire de sérialiser les données sensibles.  
  
-   **La réinitialisation.** Lorsque la classe, une structure ou un module définissant la propriété est en cours terminée, réinitialisez les données sensibles, les valeurs par défaut ou à d’autres valeurs sans signification. Cela offre une protection supplémentaire lorsque cette zone de mémoire est libérée pour l’accès général.  
  
-   **Persistance.** Ne conservent aucune donnée sensible, par exemple sur le disque, si vous pouvez l’éviter. En outre, n’écrivez pas toutes les données sensibles dans le Presse-papiers.  
  
 Le `WriteOnly` modificateur peut être utilisé dans ce contexte :  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
