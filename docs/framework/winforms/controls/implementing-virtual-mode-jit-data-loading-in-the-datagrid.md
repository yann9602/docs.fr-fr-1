---
title: "Impl&#233;mentation du mode virtuel avec le chargement de donn&#233;es juste-&#224;-temps dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "données (Windows Forms), gérer de grands groupes de données"
  - "DataGridView (contrôle Windows Forms), grands groupes de données"
  - "DataGridView (contrôle Windows Forms), mode virtuel"
  - "exemples (Windows Forms), chargement de données juste-à-temps"
  - "chargement de données juste-à-temps"
  - "mode virtuel, chargement de données juste-à-temps"
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Impl&#233;mentation du mode virtuel avec le chargement de donn&#233;es juste-&#224;-temps dans le contr&#244;le DataGridView Windows Forms
Une raison d'implémenter le mode virtuel dans le contrôle <xref:System.Windows.Forms.DataGridView> est de récupérer des données uniquement quand elles sont nécessaires  Cela est appelé *le chargement de données juste\-à\-temps*.  
  
 Si vous utilisez une table très grande dans une base de données distante, par exemple, que vous pouvez souhaiter éviter des délais de démarrage en récupérant uniquement les données qui sont nécessaires pour l'affichage et l'extraction de données supplémentaires uniquement lorsque l'utilisateur fait défiler de nouvelles lignes dans l'affichage.  Si les ordinateurs clients qui exécutent votre application ont une quantité de mémoire disponible limitée pour stocker des données, vous pouvez souhaiter également ignorer les données inutilisées lors de la récupération de nouvelles valeurs de la base de données.  
  
 Les sections suivantes décrivent comment utiliser un contrôle <xref:System.Windows.Forms.DataGridView> avec un cache juste\-à\-temps.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : implémenter le mode virtuel avec le chargement de données juste\-à\-temps dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## Le formulaire  
 L'exemple de code suivant définit un formulaire contenant un contrôle <xref:System.Windows.Forms.DataGridView> en lecture seule qui interagit avec un objet `Cache` via un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.CellValueNeeded>.  L'objet `Cache` gère les valeurs stockées localement et utilise un objet `DataRetriever` pour récupérer des valeurs de la table Orders de l'exemple de base de données Northwind.  L'objet `DataRetriever`, qui implémente l'interface `IDataPageRetriever` requise par la classe `Cache`, est également utilisé pour initialiser les lignes et les colonnes du contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 Les types `IDataPageRetriever`, `DataRetriever` et `Cache` sont décrits ultérieurement dans cette rubrique.  
  
> [!NOTE]
>  Le stockage d'informations sensibles, par exemple, un mot de passe, dans la chaîne de connexion peut affecter la sécurité de votre application.  L'utilisation de l'authentification Windows \(également appelée sécurité intégrée\) offre un moyen plus sûr de contrôler l'accès à une base de données.  Pour plus d'informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## L'interface IDataPageRetriever  
 L'exemple de code suivant définit l'interface `IDataPageRetriever` qui est implémentée par la classe `DataRetriever`.  La seule méthode déclarée dans cette interface est la méthode `SupplyPageOfData`, qui requiert un index de ligne initial et un décompte du nombre de lignes dans une seule page de données.  Ces valeurs sont utilisées par l'implémenteur pour récupérer un sous\-ensemble de données d'une source de données.  
  
 Un objet `Cache` utilise une implémentation de cette interface pendant la construction pour charger deux pages initiales de données.  Toutes les fois qu'une valeur non mise en cache est exigée, le cache ignore l'une de ces pages et demande une nouvelle page contenant la valeur de `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## La classe DataRetriever  
 L'exemple de code suivant définit la classe `DataRetriever`, qui implémente l'interface `IDataPageRetriever`, pour récupérer des pages de données d'un serveur.  La classe `DataRetriever` fournit également des propriétés `Columns` et `RowCount`, que le contrôle <xref:System.Windows.Forms.DataGridView> utilise pour créer les colonnes nécessaires et ajouter le nombre approprié de lignes vides à la collection <xref:System.Windows.Forms.DataGridView.Rows%2A>.  L'ajout de lignes vides est nécessaire pour que le contrôle se comporte comme s'il contient toutes les données de la table.  Cela signifie que la case de défilement dans la barre de défilement aura la taille appropriée, et que l'utilisateur sera à même d'accéder à toute ligne dans la table.  Les lignes sont remplies par le gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.CellValueNeeded> uniquement lorsqu'elles défilent dans l'affichage.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## La classe Cache  
 L'exemple de code suivant définit la classe `Cache` qui gère deux pages de données remplies via une implémentation `IDataPageRetriever`.  La classe `Cache` définit une structure `DataPage` interne qui contient un <xref:System.Data.DataTable> pour stocker les valeurs dans une seule page de cache qui calcule les index de ligne représentant les limites supérieures et inférieures de la page.  
  
 La classe `Cache` charge deux pages de données au moment de la construction.  Toutes les fois que l'événement <xref:System.Windows.Forms.DataGridView.CellValueNeeded> demande une valeur, l'objet `Cache` détermine si la valeur est disponible dans l'une de ses deux pages et, le cas échéant, la retourne.  Si la valeur est non disponible localement, l'objet `Cache` détermine laquelle de ses deux pages est la plus éloignée des lignes affichées actuellement et remplace la page par une nouvelle page contenant la valeur demandée qu'il retourne ensuite.  
  
 En supposant que le nombre de lignes dans une page de données est le même que le nombre de lignes pouvant être affichées à la fois à l'écran, ce modèle permet aux utilisateurs qui paginent à travers la table de retourner efficacement à la dernière page affichée.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## Considérations supplémentaires  
 Les exemples de code antérieurs sont fournis comme démonstration de chargement de données juste\-à\-temps.  Vous devrez modifier le code pour vos propres besoins pour obtenir le rendement maximal.  Au minimum, vous devrez choisir une valeur appropriée pour le nombre de lignes par page de données dans le cache.  Cette valeur est passée dans le constructeur `Cache`.  Le nombre de lignes par page ne doit pas être inférieur au nombre des lignes qui peuvent être affichées simultanément dans votre contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 Pour des résultats optimaux, vous devrez effectuer des tests de performance et de facilité d'utilisation afin de déterminer les besoins de votre système et de vos utilisateurs.  Parmi les différents facteurs que vous devez prendre en considération figurent la quantité de mémoire dans les ordinateurs clients qui exécutent votre application, la bande passante disponible de la connexion réseau utilisée et la latence du serveur utilisé.  La bande passante et la latence doivent être déterminées aux moments de l'utilisation maximale.  
  
 Pour améliorer les performances de défilement de votre application, vous pouvez augmenter la quantité de données stockées localement.  Pour améliorer le temps de démarrage, toutefois, vous devez éviter de charger trop de données initialement.  Vous pouvez modifier la classe `Cache` pour augmenter le nombre de pages de données qu'elle peut stocker.  L'utilisation d'un plus grand nombre de données peut améliorer le rendement de défilement, mais vous devrez déterminer le nombre idéal de lignes dans une page de données, selon la bande passante disponible et la latence serveur.  Avec des pages moins volumineuses, le serveur fera fréquemment l'objet d'un accès, mais prendra moins de temps pour retourner les données demandées.  Si la latence représente davantage un problème que la bande passante, vous pouvez utiliser des pages de données plus volumineuses.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>   
 [Réglage des performances dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)   
 [Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)   
 [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)   
 [Comment : implémenter le mode virtuel avec le chargement de données juste\-à\-temps dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)