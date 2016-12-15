---
title: "Type of member &#39;&lt;membername&gt;&#39; is not CLS-compliant | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40025"
  - "vbc40025"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40025"
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Type of member &#39;&lt;membername&gt;&#39; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le type de données spécifié pour ce membre ne fait pas partie du [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\).  Cette erreur ne provient pas de votre composant, parce que le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] et [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] prennent en charge ce type de données.  Toutefois, il est possible qu'un autre composant écrit dans le code strictement conforme CLS ne prenne pas en charge ce type de données.  Ce composant peut ne pas interagir avec succès avec votre composant.  
  
 Les types de données [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] suivants ne sont pas conformes CLS :  
  
-   [SByte Data Type](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong Data Type](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort Data Type](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC40025  
  
### Pour corriger cette erreur  
  
-   Si votre composant sert d'interface uniquement avec d'autres composants du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], ou ne sert pas d'interface avec d'autres composants, aucune modification n'est nécessaire.  
  
-   Si vous utilisez un composant non écrit pour le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], vous pouvez déterminer, par réflexion ou à partir de la documentation, s'il prend en charge ce type de données.  Si tel est le cas, aucune modification n'est nécessaire.  
  
-   Si vous utilisez un composant qui ne prend pas en charge ce type de données, vous devez le remplacer par le type conforme CLS le plus proche.  Par exemple, vous pouvez peut\-être utiliser `Integer` à la place d'`UInteger` si vous n'avez pas besoin de la plage de valeurs qui est supérieure à 2 147 483 647.  Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.  
  
-   Si vous utilisez des objets Automation ou COM, gardez à l'esprit que certains types ont des largeurs des données différentes de celles du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].  Par exemple, `uint` correspond souvent à 16 bits dans d'autres environnements.  Si vous passez un argument de 16 bits à un tel composant, déclarez\-le comme type de données `UShort` et non comme `UInteger` dans votre code [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] managé.  
  
## Voir aussi  
 [Réflexion](../Topic/Reflection%20in%20the%20.NET%20Framework.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)