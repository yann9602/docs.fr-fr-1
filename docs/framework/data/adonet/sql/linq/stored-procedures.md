---
title: "Procédures stockées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cff3103595ccb782e2e51313d427259c0191105d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="stored-procedures"></a>Procédures stockées
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]utilise des méthodes dans votre modèle objet pour représenter des procédures stockées dans la base de données. Vous désignez des méthodes comme des procédures stockées en appliquant l'attribut <xref:System.Data.Linq.Mapping.FunctionAttribute> et, si nécessaire, l'attribut <xref:System.Data.Linq.Mapping.ParameterAttribute>. Pour plus d’informations, consultez [le modèle LINQ to SQL objet](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] utilisent généralement le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pour mapper des procédures stockées. Les rubriques de cette section montrent comment former et appeler ces méthodes dans votre application si vous écrivez vous-même le code.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour retourner des jeux de lignes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)  
 Décrit comment retourner des lignes de données et comment utiliser un paramètre d'entrée.  
  
 [Guide pratique pour utiliser des procédures stockées qui prennent des paramètres](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-that-take-parameters.md)  
 Décrit comment utiliser des paramètres d'entrée et de sortie.  
  
 [Guide pratique pour utiliser des procédures stockées mappées pour plusieurs formes de résultats](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 Explique comment permettre le retour de plusieurs formes dans la même procédure stockée.  
  
 [Guide pratique pour utiliser des procédures stockées mappées pour des formes de résultats séquentielles](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 Explique comment permettre plusieurs formes lorsque la séquence de retour est connue.  
  
 [Personnalisation d’opérations à l’aide de procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)  
 Explique comment utiliser des procédures stockées pour implémenter les opérations d'insertion, de mise à jour et de suppression.  
  
 [Personnalisation d’opérations à l’aide de procédures stockées uniquement](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures-exclusively.md)  
 Explique comment utiliser uniquement des procédures stockées pour implémenter les opérations d'insertion, de mise à jour et de suppression.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Guide de programmation](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 Fournit des informations sur la création et l'utilisation de votre modèle objet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Procédure pas à pas : utilisation de procédures stockées uniquement (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)  
 Inclut des procédures qui expliquent comment utiliser des procédures stockées dans Visual Basic.  
  
 [Procédure pas à pas : utilisation de procédures stockées uniquement (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)  
 Inclut des procédures qui expliquent comment utiliser des procédures stockées dans C#.
