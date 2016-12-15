---
title: "Le type de la valeur facultative pour le param&#232;tre facultatif &lt;nom_param&#232;tre&gt; n’est pas conforme &#224; CLS | Microsoft Docs"
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
  - "BC40042"
  - "vbc40042"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40042"
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type de la valeur facultative pour le param&#232;tre facultatif &lt;nom_param&#232;tre&gt; n’est pas conforme &#224; CLS
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une procédure est marquée comme `<CLSCompliant(True)>` mais déclare un paramètre [facultatif](../../../visual-basic/language-reference/modifiers/optional.md) avec la valeur par défaut d’un type non conforme.  
  
 Pour qu’une procédure soit conforme à CLS ([Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)), elle doit utiliser uniquement des types conformes à CLS. Cette règle s’applique aux types des paramètres, au type de retour et aux types de toutes ses variables locales. Elle s’applique également aux valeurs par défaut des paramètres facultatifs.  
  
 Les types de données [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] suivants ne sont pas conformes CLS :  
  
-   [SByte (type de données)](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger (type de données)](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong (type de données)](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort (type de données)](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40042  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si le paramètre facultatif doit avoir une valeur par défaut de ce type particulier, supprimez <xref:System.CLSCompliantAttribute>. La procédure ne peut pas être conforme à CLS.  
  
-   Si la procédure doit être conforme à CLS, remplacez le type de cette valeur par défaut par le type conforme à CLS le plus proche. Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647. Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.  
  
-   Si vous interfacez avec des objets Automation ou COM, n’oubliez pas que certains types ont des largeurs de données différentes de celles du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Par exemple, `int` correspond souvent à 16 bits dans d’autres environnements. Si vous passez un entier sur 16 bits à un tel composant, déclarez-le comme `Short` au lieu de `Integer` dans votre code [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] managé.  
  
## <a name="see-also"></a>Voir aussi  
 [<PAVE OVER>\> Écriture d’un code conforme à CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)