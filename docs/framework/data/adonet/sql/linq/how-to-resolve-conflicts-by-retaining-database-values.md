---
title: "Comment : résoudre des conflits en conservant des valeurs de bases de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0747a4318fdab76c5fbd920f7291346d4d8ff58d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a>Comment : résoudre des conflits en conservant des valeurs de bases de données
Pour harmoniser les différences entre les valeurs de base de données attendues et réelles avant d'essayer de renvoyer vos modifications, vous pouvez utiliser <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> pour conserver les valeurs trouvées dans la base de données. Les valeurs actuelles dans le modèle objet sont alors remplacées. Pour plus d’informations, consultez [d’accès concurrentiel optimiste : vue d’ensemble](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Dans tous les cas, l'enregistrement sur le client est actualisé lors de la récupération des données mises à jour de la base de données. Cette action permet de s'assurer que la prochaine tentative de mise à jour n'échouera pas sur les mêmes vérifications d'accès concurrentiel.  
  
## <a name="example"></a>Exemple  
 Dans ce scénario, une exception <xref:System.Data.Linq.ChangeConflictException> est levée lorsque User1 tente de soumettre des modifications car User2 a modifié entre-temps les colonnes Assistant et Department. Le tableau suivant présente la situation.  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|État de la base de données d'origine lors d'une interrogation par User1 et User2.|Alfreds|Maria|Sales|  
|User1 s'apprête à soumettre ces modifications.|Alfred||Marketing|  
|User2 a déjà soumis ces modifications.||Mary|Service|  
  
 User1 décide de résoudre ce conflit en remplaçant les valeurs actuelles dans le modèle objet par les valeurs de base de données les plus récentes.  
  
 Lorsque User1 résout le conflit à l'aide de <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, le résultat dans la base de données se présente comme dans le tableau suivant :  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|Nouvel état après résolution du conflit.|Alfreds<br /><br /> (d'origine)|Mary<br /><br /> (de User2)|Service<br /><br /> (de User2)|  
  
 Le code d'exemple suivant indique comment remplacer les valeurs actuelles dans le modèle objet par les valeurs de base de données. Aucune inspection ni aucune gestion personnalisée des conflits de membres individuels n'est effectuée.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
