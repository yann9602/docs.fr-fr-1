---
title: "Atténuation : Validation du schéma XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cd5e83da32e32b60f5d1584c7057e36a3851b8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-xml-schema-validation"></a>Atténuation : Validation du schéma XML
Dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], la validation de schéma XSD détecte une violation de la contrainte unique si une clé composée est utilisée et qu'une clé est vide.  
  
## <a name="impact"></a>Impact  
 L'impact de cette modification devrait être minime : selon la spécification de schéma, une erreur de validation de schéma est attendue si `xsd:unique` est enfreinte par l'utilisation d'une clé composée avec une clé vide.  
  
## <a name="mitigation"></a>Atténuation  
 Le fait qu'une erreur de validation de schéma soit détectée ou pas si une clé composée a une clé vide est une fonctionnalité que vous pouvez configurer :  
  
-   Depuis les applications qui ciblent le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], la détection de l'erreur de validation de schéma est activée par défaut ; néanmoins, il est possible de la refuser afin que l'erreur de validation de schéma ne soit pas détectée.  
  
-   Depuis les applications qui s'exécutent sous le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] mais ciblent le [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] ou version antérieure, la détection de l'erreur de validation de schéma n'est pas activée par défaut ; néanmoins, il est possible de l'activer afin que l'erreur de validation de schéma soit détectée.  
  
 Ce comportement peut être configuré en utilisant la classe <xref:System.AppContext> pour définir la valeur du commutateur `System.Xml.IgnoreEmptyKeySequences`. Comme la valeur du commutateur par défaut est `false` (les séquences de touches vides ne sont pas ignorées), les applications qui ciblent le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] peuvent désactiver le comportement en utilisant le code suivant pour définir le commutateur avec la valeur `true` :  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 Pour les applications qui ciblent les versions [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] et antérieures, comme la valeur du commutateur par défaut est `true` (les séquences de touches vides sont ignorées), il est possible de garantir qu'une clé composée avec une clé vide génère bel et bien une erreur de validation de schéma en utilisant le code suivant pour définir le commutateur avec la valeur `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
