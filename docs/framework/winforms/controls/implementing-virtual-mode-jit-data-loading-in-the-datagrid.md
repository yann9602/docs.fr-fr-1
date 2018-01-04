---
title: "Implémentation du mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a830c11e8df73b71f16c1b9dfd1007461d910f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Implémentation du mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms
L’une des raisons pour implémenter le mode virtuel dans le <xref:System.Windows.Forms.DataGridView> contrôle consiste à récupérer des données uniquement qu’il est nécessaire. Il s’agit *lors du chargement de données juste-à-temps*.  
  
 Si vous travaillez avec une table très volumineuse dans une base de données distante, par exemple, vous souhaiterez éviter les retards de démarrage en récupérant uniquement les données qui sont nécessaires pour l’affichage et la récupération des données supplémentaires uniquement lorsque l’utilisateur fait défiler de nouvelles lignes dans la vue. Si les ordinateurs clients qui exécutent votre application ont une quantité limitée de mémoire disponible pour le stockage des données, vous souhaiterez également ignorer les données inutilisées lors de la récupération de nouvelles valeurs à partir de la base de données.  
  
 Les sections suivantes décrivent comment utiliser un <xref:System.Windows.Forms.DataGridView> contrôle avec un cache juste-à-temps.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : implémenter le Mode virtuel avec le chargement de données juste à temps dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="the-form"></a>Le formulaire  
 L’exemple de code suivant définit un formulaire contenant en lecture seule <xref:System.Windows.Forms.DataGridView> contrôle interagit avec un `Cache` via un <xref:System.Windows.Forms.DataGridView.CellValueNeeded> Gestionnaire d’événements. Le `Cache` objet gère les valeurs stockées localement et utilise un `DataRetriever` objet pour récupérer les valeurs de la table Orders de la base de données exemple Northwind. Le `DataRetriever` objet qui implémente le `IDataPageRetriever` interface requise par le `Cache` de classes, est également utilisé pour initialiser le <xref:System.Windows.Forms.DataGridView> contrôler les lignes et colonnes.  
  
 Le `IDataPageRetriever`, `DataRetriever`, et `Cache` types sont décrits plus loin dans cette rubrique.  
  
> [!NOTE]
>  Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>L’Interface IDataPageRetriever  
 L’exemple de code suivant définit la `IDataPageRetriever` interface, qui est implémentée par la `DataRetriever` classe. La seule méthode déclarée dans cette interface est le `SupplyPageOfData` (méthode), ce qui nécessite un index de ligne initial et le nombre de lignes dans une seule page de données. Ces valeurs sont utilisées par l’implémenteur pour récupérer un sous-ensemble de données à partir d’une source de données.  
  
 A `Cache` objet utilise une implémentation de cette interface pendant la construction pour charger des deux premières pages de données. Chaque fois qu’une valeur n’est nécessaire, le cache ignore l’une de ces pages et demande une nouvelle page contenant la valeur de la `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>La classe DataRetriever  
 L’exemple de code suivant définit la `DataRetriever` classe qui implémente le `IDataPageRetriever` interface pour récupérer des pages de données à partir d’un serveur. Le `DataRetriever` classe fournit également `Columns` et `RowCount` propriétés, ce qui le <xref:System.Windows.Forms.DataGridView> contrôle utilise pour créer les colonnes nécessaires et ajouter le nombre approprié de lignes vides pour la <xref:System.Windows.Forms.DataGridView.Rows%2A> collection. Ajout de lignes vides est nécessaire afin que le contrôle se comporte comme s’il contient toutes les données dans la table. Cela signifie que la case de défilement dans la barre de défilement aura la taille appropriée, et l’utilisateur sera en mesure d’accéder n’importe quelle ligne dans la table. Les lignes sont remplies par le <xref:System.Windows.Forms.DataGridView.CellValueNeeded> Gestionnaire d’événements uniquement lorsqu’ils sont devient visible.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>La classe de Cache  
 L’exemple de code suivant définit la `Cache` (classe), qui gère deux pages de données remplies via une `IDataPageRetriever` implémentation. Le `Cache` classe définit une exception interne `DataPage` structure qui contient un <xref:System.Data.DataTable> pour stocker les valeurs dans un seul cache qui calcule les index de ligne et page représentent les limites supérieures et inférieures de la page.  
  
 La `Cache` classe charge deux pages de données au moment de la construction. Chaque fois que le <xref:System.Windows.Forms.DataGridView.CellValueNeeded> événement demande une valeur, le `Cache` objet détermine si la valeur est disponible dans un de ses deux pages et, dans ce cas, elle retourne. Si la valeur n’est pas disponible localement, le `Cache` objet détermine laquelle de ses deux pages plus éloigné de lignes actuellement affichées et remplace la page par un autre qui contient la valeur demandée qu’il retourne ensuite.  
  
 En supposant que le nombre de lignes dans une page de données est le même que le nombre de lignes qui peuvent être affichés à l’écran à la fois, ce modèle permet aux utilisateurs la pagination via la table de retourner efficacement à la dernière page affichée.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Considérations supplémentaires  
 Les exemples de code précédents sont fournis comme démonstration de chargement de données juste-à-temps. Vous devez modifier le code pour vos propres besoins pour obtenir une efficacité maximale. Au minimum, vous devez choisir une valeur appropriée pour le nombre de lignes par page de données dans le cache. Cette valeur est passée dans le `Cache` constructeur. Le nombre de lignes par page doit être non inférieur au nombre de lignes qui peuvent être affichées simultanément dans votre <xref:System.Windows.Forms.DataGridView> contrôle.  
  
 Pour de meilleurs résultats, vous devez effectuer des tests de performances et facilité d’utilisation pour déterminer les besoins de votre système et de vos utilisateurs. Vous devez impérativement prendre en compte plusieurs facteurs incluent la quantité de mémoire dans les ordinateurs clients exécutant votre application, la bande passante disponible de la connexion réseau utilisée et la latence du serveur utilisé. La bande passante et la latence doivent être déterminées à des moments d’utilisation maximale.  
  
 Pour améliorer les performances de défilement de votre application, vous pouvez augmenter la quantité de données stockées localement. Pour améliorer les temps de démarrage, toutefois, vous devez éviter de charger trop de données initialement. Il pouvez que vous souhaitez modifier la `Cache` classe pour augmenter le nombre de pages de données qu’elle peut stocker. L’utilisation de plusieurs pages de données peut améliorer l’efficacité de défilement, mais vous devrez déterminer le nombre idéal de lignes dans une page de données, en fonction de la bande passante disponible et la latence du serveur. Avec des pages plus petites, le serveur est plus accessible, mais nécessite moins de temps pour retourner les données demandées. Si la latence est un problème que la bande passante, vous souhaiterez probablement utiliser les pages de données plus volumineux.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [Réglage des performances dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [Guide pratique pour implémenter le mode virtuel avec le chargement immédiat des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
