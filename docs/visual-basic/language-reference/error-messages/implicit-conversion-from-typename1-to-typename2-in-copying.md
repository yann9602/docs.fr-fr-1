---
title: "Conversion implicite de &quot;&lt;NomType1&gt;&quot;à&quot;&lt;NomType2&gt;« en copiant la valeur du paramètre &quot;ByRef&quot; &quot;&lt;parametername&gt;&quot; dans l’argument correspondant. | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
dev_langs:
- VB
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: 7
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e397241aab78e17ea4efde0ea682d0e237fb8f8a
ms.lasthandoff: 03/13/2017

---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>Conversion implicite de '&lt;NomType1&gt;'à'&lt;NomType2&gt;« en copiant la valeur du paramètre 'ByRef' '&lt;parametername&gt;' dans l’argument correspondant.
Une procédure est appelée avec un [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument d’un type différent de celui de son paramètre correspondant.  
  
 Si vous passez un argument `ByRef`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copie parfois sa valeur dans une variable locale de la procédure au lieu de passer une référence. Dans ce cas, la procédure retourne [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit copier la valeur de variable locale dans l’argument dans le code appelant.  
  
 Si une valeur d’argument `ByRef` est copiée dans la procédure, et si l’argument et le paramètre sont du même type, aucune conversion n’est nécessaire. Mais si les types sont différents, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit convertir dans les deux sens. Étant donné que vous ne pouvez pas utiliser `CType` ou un des autres mots clés de conversion sur un argument de procédure ou de paramètre, une telle conversion est toujours implicite.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC41999  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si possible, utilisez un argument d’appel du même type que le paramètre de procédure, par conséquent, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne doit pas effectuer de conversion.  
  
-   Si vous avez besoin d’appeler la procédure avec un argument de type différent du type de paramètre, mais n’avez pas besoin de retourner une valeur dans l’argument d’appel, de définir le paramètre pour être [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) au lieu de `ByRef`.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Arguments et paramètres de procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passage des Arguments par valeur et par référence](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
