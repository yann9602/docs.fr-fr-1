---
title: "&#201;tats des objets et suivi des modifications | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# &#201;tats des objets et suivi des modifications
Les objets [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] participent toujours dans un certain *état*.  Par exemple, lorsque [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] crée un objet, l'état de l'objet est `Unchanged`.  Lorsque vous créez un objet, celui\-ci est inconnu pour <xref:System.Data.Linq.DataContext> et son état est `Untracked`.  Après l'exécution réussie de <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, l'état de tous les objets connus dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] est `Unchanged`.  La seule exception est représentée par les objets qui ont été supprimés de la base de données, dont l'état est `Deleted`, et qui sont inutilisables dans cette instance <xref:System.Data.Linq.DataContext>.  
  
## États des objets  
 Le tableau suivant répertorie les états possibles pour les objets [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
|État|Description|  
|----------|-----------------|  
|`Untracked`|Objet non suivi par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  Exemples :<br /><br /> -   Objet non interrogé dans le <xref:System.Data.Linq.DataContext> actuel \(par exemple, un objet créé récemment\).<br />-   Objet créé par désérialisation<br />-   Objet interrogé par un <xref:System.Data.Linq.DataContext> différent.|  
|`Unchanged`|Objet récupéré en utilisant le <xref:System.Data.Linq.DataContext> actuel et dont aucune modification n'est connue depuis sa création.|  
|`PossiblyModified`|Objet *attaché* à un <xref:System.Data.Linq.DataContext>.  Pour plus d'informations, consultez [Récupération de données et opérations CUD dans les applications multicouches \(LINQ to SQL\)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).|  
|`ToBeInserted`|Objet qui n'est pas récupéré en utilisant le <xref:System.Data.Linq.DataContext> actuel.  Cela entraîne un `INSERT` dans la base de données pendant <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeUpdated`|Objet dont la modification est connue depuis sa récupération.  Cela entraîne un `UPDATE` dans la base de données pendant <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeDeleted`|Objet marqué pour être supprimé, ce qui entraîne une `DELETE` de la base de données pendant <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`Deleted`|Objet supprimé dans la base de données.  Cet état est définitif et n'autorise pas de transitions supplémentaires.|  
  
## Insertion d'objets  
 Vous pouvez demander explicitement des `Inserts` à l'aide de <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] peut également déduire les `Inserts` en recherchant des objets connectés à l'un des objets connus qui doit être mis à jour.  Par exemple, si vous ajoutez un objet `Untracked` à un <xref:System.Data.Linq.EntitySet%601> ou si vous affectez un <xref:System.Data.Linq.EntityRef%601> à un objet `Untracked`, l'objet `Untracked` devient accessible à l'aide d'objets suivis dans le graphique.  Lors du traitement de <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] parcourt les objets suivis et identifie tous les objets persistants accessibles qui ne sont pas suivis.  Ces objets peuvent être insérés dans la base de données.  
  
 Pour les classes d'une hiérarchie d'héritage, <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> \(`o`\) définit également la valeur du membre désigné comme *discriminateur* pour correspondre au type de l'objet `o`.  La valeur du discriminateur est par conséquent substituée par la valeur par défaut si un type correspond à la valeur du discriminateur par défaut.  Pour plus d'informations, consultez [Prise en charge de l'héritage](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
> [!IMPORTANT]
>  Un objet ajouté à un `Table` n'est pas dans le cache d'identité.  Le cache d'identité reflète uniquement ce qui est récupéré de la base de données.  Après un appel à <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>, l'entité ajoutée n'apparaît pas dans les requêtes sur la base de données tant que <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ne s'est pas terminé avec succès.  
  
## Suppression d'objets  
 Vous pouvez marquer un objet suivi `o` pour le supprimer en appelant <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> \(o\) sur le type <xref:System.Data.Linq.Table%601> approprié.  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] considère la suppression d'un objet d'un <xref:System.Data.Linq.EntitySet%601> comme une opération de mise à jour et la valeur de clé étrangère correspondante est Null.  La cible de l'opération \(`o`\) n'est pas supprimée de sa table.  Par exemple, `cust.Orders.DeleteOnSubmit(ord)` indique une mise à jour où la relation entre `cust` et `ord` est rompue en affectant à la clé étrangère `ord.CustomerID` la valeur null.  Cela n'entraîne pas la suppression de la ligne qui correspond à `ord`.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] effectue le traitement suivant lorsqu'un objet est supprimé \(<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>\) de sa table :  
  
-   Lorsque <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelé, une opération de `DELETE` est effectuée pour cet objet.  
  
-   La suppression n'est pas propagée aux objets connexes, qu'ils soient chargés ou non.  Plus précisément, les objets connexes ne sont pas chargés pour mettre à jour la propriété de relation.  
  
-   Après l'exécution réussie de <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, l'état des objets est `Deleted`.  Par conséquent, vous ne pouvez pas utiliser l'objet ou son `id` dans ce <xref:System.Data.Linq.DataContext>.  Le cache interne maintenu par une instance <xref:System.Data.Linq.DataContext> n'élimine pas les objets qui sont récupérés ou ajoutés comme nouveaux, même après que les objets ont été supprimés dans la base de données.  
  
 Vous pouvez appeler <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> uniquement sur un objet suivi par le <xref:System.Data.Linq.DataContext>.  Pour un objet `Untracked`, vous devez appeler <xref:System.Data.Linq.Table%601.Attach%2A> avant d'appeler <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>.  L'appel à <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> sur un objet `Untracked` lève une exception.  
  
> [!NOTE]
>  La suppression d'un objet d'une table indique à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de générer une commande SQL `DELETE` correspondante au moment de <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  Cette action ne supprime pas l'objet du cache ou ne propage pas la suppression aux objets connexes.  
>   
>  Pour récupérer l'`id` d'un objet supprimé, utilisez une nouvelle instance <xref:System.Data.Linq.DataContext>.  Pour nettoyer des objets connexes, vous pouvez utiliser la fonctionnalité de *suppression en cascade* de la base de données ou supprimer manuellement les objets connexes.  
>   
>  Les objets connexes ne doivent pas être supprimés dans un ordre particulier \(contrairement aux bases de données\).  
  
## Mise à jour d'objets  
 Vous pouvez détecter les `Updates` en observant les notifications de modifications.  Les notifications sont fournies par l'événement <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> dans les accesseurs Set de propriété.  Lorsque [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] est informé de la première modification d'un objet, il crée une copie de l'objet et considère l'objet comme candidat pour générer une instruction `Update`.  
  
 Pour les objets qui n'implémentent pas <xref:System.ComponentModel.INotifyPropertyChanging>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] conserve une copie des valeurs des objets lors de leur matérialisation.  Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] compare les valeurs actuelles et d'origine pour décider si l'objet a été modifié.  
  
 Pour les mises à jour de relations, la référence de l'enfant au parent \(autrement dit, la référence qui correspond à la clé étrangère\) est considérée comme l'autorité.  La référence dans le sens inverse \(autrement dit, du parent à l'enfant\) est facultative.  Les classes de relation \(<xref:System.Data.Linq.EntitySet%601> et <xref:System.Data.Linq.EntityRef%601>\) garantissent la cohérence des références bidirectionnelles pour les relations de type un\-à\-plusieurs et un\-à\-un.  Si le modèle objet n'utilise pas <xref:System.Data.Linq.EntitySet%601> ou <xref:System.Data.Linq.EntityRef%601> et si la référence inverse est présente, vous devez respecter la cohérence avec la référence vers l'avant lorsque la relation est mise à jour.  
  
 Si vous mettez à jour à la fois la référence requise et la clé étrangère correspondante, vous devez vous assurer de leur correspondance.  Une exception <xref:System.InvalidOperationException> est levée si elles ne sont pas toutes les deux synchronisés au moment où vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  Bien que les modifications de valeur de clé étrangère soient suffisantes pour affecter une mise à jour de ligne sous\-jacente, vous devez modifier la référence pour maintenir la connectivité du graphique d'objet et la cohérence bidirectionnelle des relations.  
  
## Voir aussi  
 [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [Opérations d'insertion, de mise à jour et de suppression](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)