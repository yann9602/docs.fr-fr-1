---
title: "Conversion implicite de &#39; &lt;nom_type1&gt;&#39; à &#39;&lt; nom_type2&gt;&#39; lors de la copie de la valeur des &#39; ByRef &#39; paramètre &#39; &lt;nom_paramètre&gt;&#39; retour à l’argument correspondant."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords: BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e858b475a816a35d18822643de5a273abe28562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>Conversion implicite de &#39; &lt;nom_type1&gt;&#39; à &#39;&lt; nom_type2&gt;&#39; lors de la copie de la valeur des &#39; ByRef &#39; paramètre &#39; &lt;nom_paramètre&gt;&#39; retour à l’argument correspondant.
Une procédure est appelée avec un [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument d’un type différent de celui de son paramètre correspondant.  
  
 Si vous passez un argument `ByRef`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] copie parfois la valeur d’argument dans une variable locale de la procédure au lieu de passer une référence. Dans ce cas, quand la procédure est retournée, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doit recopier la valeur de la variable locale dans l’argument du code appelant.  
  
 Si une valeur d’argument `ByRef` est copiée dans la procédure, et si l’argument et le paramètre sont du même type, aucune conversion n’est nécessaire. Toutefois, si les types sont différents, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doit effectuer une conversion dans les deux sens. Étant donné que vous ne pouvez pas utiliser `CType` ou une des autres mots clés de conversion sur un argument de procédure ou de paramètre, une telle conversion est toujours implicite.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC41999  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si possible, utilisez un argument d’appel du même type que celui du paramètre de procédure, pour que [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] n’ait pas besoin d’effectuer de conversion.  
  
-   Si vous avez besoin d’appeler la procédure avec un argument de type différent du type de paramètre, mais n’avez pas besoin de retourner une valeur dans l’argument d’appel, définissez le paramètre [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) au lieu de `ByRef`.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Paramètres et arguments d’une procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Passage d’un argument par valeur et par référence](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
