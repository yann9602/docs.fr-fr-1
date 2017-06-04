---
title: "Proc&#233;dure&#160;: r&#233;soudre les conflits en fusionnant des valeurs de base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: r&#233;soudre les conflits en fusionnant des valeurs de base de donn&#233;es
Pour harmoniser des différences entre des valeurs de base de données attendues et réelles avant de soumettre à nouveau vos modifications, vous pouvez utiliser <xref:System.Data.Linq.RefreshMode> pour fusionner des valeurs de base de données avec les valeurs de membre client actuelles.  Pour plus d'informations, consultez [Accès concurrentiel optimiste : vue d'ensemble](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Dans tous les cas, l'enregistrement sur le client est actualisé lors de la récupération des données mises à jour de la base de données.  Cette action permet de s'assurer que la prochaine tentative de mise à jour n'échouera pas sur les mêmes vérifications d'accès concurrentiel.  
  
## Exemple  
 Dans ce scénario, une exception <xref:System.Data.Linq.ChangeConflictException> est levée lorsque User1 tente de soumettre des modifications car User2 a modifié entre\-temps les colonnes Assistant et Department.  Le tableau suivant présente la situation.  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|État de la base de données d'origine lors d'une interrogation par User1 et User2.|Alfreds|Maria|Sales|  
|User1 s'apprête à soumettre ces modifications.|Alfred||Marketing|  
|User2 a déjà soumis ces modifications.||Mary|Service|  
  
 User1 décide de résoudre ce conflit en fusionnant des valeurs de base de données avec les valeurs de membre client actuelles.  Les valeurs de base de données seront donc remplacées uniquement lorsque l'ensemble de modifications actuel aura également modifié cette valeur.  
  
 Lorsque User1 résout le conflit à l'aide de <xref:System.Data.Linq.RefreshMode>, le résultat dans la base de données se présente comme dans le tableau suivant :  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|Nouvel état après résolution du conflit.|Alfred<br /><br /> \(de User1\)|Mary<br /><br /> \(de User2\)|Marketing<br /><br /> \(de User1\)|  
  
 L'exemple suivant montre comment fusionner des valeurs de base de données avec les valeurs de membre client actuelles \(à moins que le client ait également modifié cette valeur\).  Aucune inspection ni aucune gestion personnalisée des conflits de membres individuels n'est effectuée.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## Voir aussi  
 [Procédure : résoudre des conflits en remplaçant des valeurs de base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)   
 [Procédure : résoudre des conflits en conservant des valeurs de base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)   
 [Procédure : gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)