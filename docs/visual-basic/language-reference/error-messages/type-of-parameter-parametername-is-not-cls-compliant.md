---
title: "Type of parameter &#39;&lt;parametername&gt;&#39; is not CLS-compliant | Microsoft Docs"
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
  - "vbc40028"
  - "bc40028"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40028"
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Type of parameter &#39;&lt;parametername&gt;&#39; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une procédure est marquée comme `<CLSCompliant(True)>` mais déclare un paramètre avec un type marqué comme `<CLSCompliant(False)>`, non marqué ou non qualifié à cause de sa non conformité.  
  
 Pour qu'une procédure soit conforme [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), elle ne doit utiliser que des types conformes CLS.  Cette règle s'applique aux types des paramètres, au type de retour et aux types de toutes ses variables locales.  
  
 Les types de données [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] suivants ne sont pas conformes CLS :  
  
-   [SByte Data Type](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong Data Type](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort Data Type](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Lorsque vous appliquez <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l'attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité.  Il n'existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n'appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC40028  
  
### Pour corriger cette erreur  
  
-   Si la procédure doit prendre un paramètre de ce type particulier, supprimez l'<xref:System.CLSCompliantAttribute>.  La procédure ne peut pas être conforme CLS.  
  
-   Si la procédure doit être conforme CLS, remplacez le type de ce paramètre par le type conforme CLS le plus proche.  Par exemple, vous pouvez peut\-être utiliser `Integer` à la place d'`UInteger` si vous n'avez pas besoin de la plage de valeurs qui est supérieure à 2 147 483 647.  Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.  
  
-   Si vous utilisez des objets Automation ou COM, gardez à l'esprit que certains types ont des largeurs des données différentes de celles du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].  Par exemple, `int` correspond souvent à 16 bits dans d'autres environnements.  Si vous passez un argument de 16 bits à un tel composant, déclarez\-le comme type de données `Short` et non comme `Integer` dans votre code managé [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## Voir aussi  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)