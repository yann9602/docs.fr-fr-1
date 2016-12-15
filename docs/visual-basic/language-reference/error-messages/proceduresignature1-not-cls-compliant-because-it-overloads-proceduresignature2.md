---
title: "&lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40035"
  - "bc40035"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40035"
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une procédure ou une propriété est marquée comme `<CLSCompliant(True)>` lorsqu'elle substitue une autre procédure ou propriété et que la seule différence entre leurs listes de paramètres est le niveau d'imbrication d'un tableau en escalier ou le rang d'un tableau.  
  
 Dans les déclarations suivantes, les deuxième et troisième déclarations génèrent cette erreur.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 La deuxième déclaration remplace le paramètre unidimensionnel d'origine `arrayParam` par un tableau de tableaux.  La troisième déclaration remplace `arrayParam` par un tableau à deux dimensions \(rang 2\).  Bien que Visual Basic autorise les surcharges à différer uniquement par l'une de ces modifications, une telle surcharge n'est pas conforme au [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\).  
  
 Lorsque vous appliquez <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l'attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité.  Il n'existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n'appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC40035  
  
### Pour corriger cette erreur  
  
-   Si la conformité CLS est requise, définissez vos surcharges pour qu'elles diffèrent les unes des autres autrement que par les seules modifications mentionnées dans cette page d'aide.  
  
-   Si les surcharges doivent différer uniquement par les modifications mentionnées dans cette page d'aide, supprimez <xref:System.CLSCompliantAttribute> de leurs définitions ou marquez\-les comme `<CLSCompliant(False)>`.  
  
## Voir aussi  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)