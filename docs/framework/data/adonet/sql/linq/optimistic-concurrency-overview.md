---
title: "Acc&#232;s concurrentiel optimiste&#160;: vue d&#39;ensemble | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Acc&#232;s concurrentiel optimiste&#160;: vue d&#39;ensemble
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge le contrôle d'accès concurrentiel optimiste.  Le tableau suivant décrit les termes applicables à l'accès concurrentiel optimiste dans la documentation de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :  
  
|Termes|Description|  
|------------|-----------------|  
|concurrence|Situation dans laquelle deux utilisateurs ou plus essaient simultanément de mettre à jour la même ligne de base de données.|  
|conflit d'accès concurrentiel|Situation dans laquelle deux utilisateurs ou plus essaient simultanément de soumettre des valeurs incompatibles à une ou plusieurs colonnes d'une ligne.|  
|contrôle d'accès concurrentiel|Technique utilisée pour résoudre des conflits d'accès concurrentiel.|  
|contrôle concurrentiel optimiste|Technique qui recherche d'abord si d'autres transactions ont modifié les valeurs d'une ligne avant d'autoriser la soumission des modifications.<br /><br /> Effectuez une comparaison avec le *contrôle d'accès concurrentiel pessimiste*, qui verrouille l'enregistrement pour éviter les conflits d'accès concurrentiel.<br /><br /> Le contrôle *optimiste* est appelé ainsi car il considère que les risques qu'une transaction interfère avec une autre sont faibles.|  
|résolution de conflit|Processus d'actualisation d'un élément en conflit en interrogeant de nouveau la base de données, puis en harmonisant les différences.<br /><br /> Lorsqu'un objet est actualisé, le dispositif de suivi des modifications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] contient les données suivantes :<br /><br /> -   Valeurs provenant initialement de la base de données et utilisées pour la vérification des mises à jour.<br />-   Nouvelles valeurs de base de données de la requête suivante.<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] détermine ensuite si l'objet est en conflit \(c'est\-à\-dire, si une ou plusieurs de ses valeurs membres ont été modifiées\).  Si l'objet est en conflit, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] détermine ensuite lesquels de ses membres sont en conflit.<br /><br /> Tout conflit entre membres que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] découvre est ajouté à une liste de conflits.|  
  
 Dans le modèle objet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], un *conflit d'accès concurrentiel optimiste* se produit lorsque les deux conditions suivantes sont vraies :  
  
-   Le client tente de soumettre des modifications à la base de données.  
  
-   Une ou plusieurs valeurs de vérification de mise à jour ont été mises à jour dans la base de données depuis la dernière fois que le client les a lues.  
  
 La résolution de ce conflit inclut la découverte des membres de l'objet qui sont en conflit, puis la décision relative à l'action que vous souhaitez effectuer.  
  
> [!NOTE]
>  Seuls les membres mappés comme <xref:System.Data.Linq.Mapping.UpdateCheck> ou <xref:System.Data.Linq.Mapping.UpdateCheck> participent aux contrôles d'accès concurrentiel optimiste.  Aucun contrôle n'est effectué pour les membres marqués <xref:System.Data.Linq.Mapping.UpdateCheck>.  Pour plus d'informations, consultez <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## Exemple  
 Par exemple, dans le scénario suivant, User1 commence à préparer une mise à jour en interrogeant la base de données pour une ligne.  User1 reçoit une ligne avec les valeurs Alfreds, Maria et Sales.  
  
 User1 souhaite modifier la valeur de la colonne Manager en Alfred et la valeur de la colonne Department en Marketing.  Avant que User1 puisse soumettre ces modifications, User2 a soumis des modifications à la base de données.  Désormais, la valeur de la colonne Assistant a donc été modifiée en Mary et la valeur de la colonne Department en Service.  
  
 Lorsque User1 tente à présent de soumettre des modifications, la soumission échoue et une exception <xref:System.Data.Linq.ChangeConflictException> est levée.  Ce résultat se produit car les valeurs de base de données des colonnes Assistant et Department ne sont pas celles qui étaient attendues.  Les membres représentant les colonnes Assistant et Department sont en conflit.  Le tableau suivant récapitule la situation :  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|État d'origine|Alfreds|Maria|Sales|  
|Utilisateur1|Alfred||Marketing|  
|User2||Mary|Service|  
  
 Vous pouvez résoudre des conflits comme celui\-ci de différentes façons.  Pour plus d'informations, consultez [Procédure : gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## Détection de conflit et liste de vérification de résolution  
 Vous pouvez détecter et résoudre des conflits à n'importe quel niveau de détail.  Une approche consiste à résoudre tous les conflits à l'aide d'une des trois façons \(consultez <xref:System.Data.Linq.RefreshMode>\) sans considération supplémentaire.  Une autre approche consiste à désigner une action spécifique pour chaque type de conflit sur tous les membres en conflit.  
  
-   Spécifiez ou modifiez des options <xref:System.Data.Linq.Mapping.UpdateCheck> dans votre modèle objet.  
  
     Pour plus d'informations, consultez [Procédure : spécifier les membres dont les conflits d'accès concurrentiel doivent être vérifiés](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
-   Dans le bloc try\/catch de votre appel à <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, spécifiez à quel point vous souhaitez que les exceptions soient levées.  
  
     Pour plus d'informations, consultez [Procédure : spécifier le moment où des exceptions d'accès concurrentiel sont levées](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
-   Déterminez la quantité de détails du conflit que vous souhaitez récupérer et incluez le code dans votre bloc try\/catch en conséquence.  
  
     Pour plus d’informations, consultez [Procédure : récupérer des informations sur les conflits entre entités](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md) et [Procédure : récupérer des informations sur les conflits entre membres](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md).  
  
-   Incluez dans votre code `try`\/`catch` la façon dont vous souhaitez résoudre les différents conflits que vous découvrez.  
  
     Pour plus d'informations, consultez [Procédure : résoudre des conflits en conservant des valeurs de base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md), [Procédure : résoudre des conflits en remplaçant des valeurs de base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md) et [Procédure : résoudre les conflits en fusionnant des valeurs de base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md).  
  
## Types LINQ to SQL qui prennent en charge la découverte et la résolution de conflits  
 Les classes et les fonctionnalités pour prendre en charge la résolution de conflits dans l'accès concurrentiel optimiste dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] incluent les éléments suivants :  
  
-   <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.MemberChangeConflict?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.ChangeConflictException?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.RefreshMode?displayProperty=fullName>  
  
## Voir aussi  
 [Procédure : gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)