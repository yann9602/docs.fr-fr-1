---
title: "Sémantique Null"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6786c7ea4441b1a753d6f0b4213f40fa64dcb4ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="null-semantics"></a>Sémantique Null
Le tableau suivant fournit des liens vers différentes parties de la documentation de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] où les problèmes relatifs à `null` (`Nothing` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) sont abordés.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Incompatibilité entre types SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|La section « Sémantique Null » de cette rubrique inclut une présentation des expressions booléennes SQL à trois valeurs par rapport aux valeurs <xref:System.Boolean>Common Language Runtime (CLR), `Nothing` littéral ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) et `null` (C#) ainsi que d'autres problèmes semblables.|  
|[Traduction des opérateurs de requête standard](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|La section « Sémantique Null » de cette rubrique décrit la sémantique de comparaison Null dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|[System.String, méthodes](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|La section « Différences par rapport à .NET » de cette rubrique décrit comment un retour de 0 de <xref:System.String.LastIndexOf%2A> peut signifier que la chaîne a la valeur null ou que la position trouvée est 0.|  
|[Calculer la somme de valeurs dans une séquence numérique](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|Décrit comment l'opérateur <xref:System.Linq.Enumerable.Sum%2A> prend la valeur `null` (`Nothing` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) au lieu de 0 pour une séquence qui contient uniquement des valeurs null ou pour une séquence vide.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et types de données](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
