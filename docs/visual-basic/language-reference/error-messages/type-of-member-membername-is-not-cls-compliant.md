---
title: "Type de membre &#39; &lt;membername&gt;&#39; n’est pas conforme CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords: BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9f7121d4787ce36feb6de5f08ca60a4419877f98
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="type-of-member-39ltmembernamegt39-is-not-cls-compliant"></a>Type de membre &#39; &lt;membername&gt;&#39; n’est pas conforme CLS
Le type de données spécifié pour ce membre n’est pas dans le cadre de la [indépendance du langage et composants indépendants du langage](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS). Cela n’est pas une erreur dans votre composant, parce que le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] et [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] prennent en charge ce type de données. Toutefois, un autre composant écrit dans un code strictement conforme CLS ne prenne pas en charge ce type de données. Ce composant n’est peut-être pas en mesure d’interagir correctement avec votre composant.  
  
 Les types de données [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] suivants ne sont pas conformes CLS :  
  
-   [SByte (type de données)](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger (type de données)](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong (type de données)](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort (type de données)](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [configuration des avertissements en Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40025  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si votre composant sert d’interface uniquement avec d’autres [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] composants, ou ne pas d’interface avec d’autres composants, vous n’avez pas besoin de rien modifier.  
  
-   Si vous utilisez un composant non écrit pour le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], vous serez peut-être en mesure de déterminer, par réflexion ou à partir de la documentation, si elle prend en charge ce type de données. Dans ce cas, il est inutile d’apporter de modifications.  
  
-   Si vous utilisez un composant qui ne prend pas en charge ce type de données, vous devez le remplacer par le type conforme CLS le plus proche. Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647. Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.  
  
-   Si vous interfacez avec des objets Automation ou COM, n’oubliez pas que certains types ont des largeurs de données différentes de celles du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Par exemple, `uint` correspond souvent à 16 bits dans d’autres environnements. Si vous passez un argument de 16 bits à un tel composant, déclarez-le en tant que `UShort` au lieu de `UInteger` dans votre managé [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.  
  
## <a name="see-also"></a>Voir aussi  
 [Réflexion](../../../framework/reflection-and-codedom/reflection.md)  
 [\<PAVE sur > écriture d’un Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
