---
title: "Procédure pas à pas : mise en cache de données d'application dans une application WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c04a2860b46460065a09de3dafedc7010753d36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>Procédure pas à pas : mise en cache de données d'application dans une application WPF
La mise en cache vous permet de stocker des données en mémoire pour y accéder rapidement. Lorsque vous accédez à nouveau les données, les applications peuvent obtenir les données à partir du cache à la place de la récupération à partir de la source d’origine. Cela peut améliorer les performances et la scalabilité. La mise en cache rend également les données disponibles quand la source de données est temporairement indisponible.  
  
 Le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fournit des classes qui vous permettent d’utiliser la mise en cache dans [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications. Ces classes sont situés dans le <xref:System.Runtime.Caching> espace de noms.  
  
> [!NOTE]
>  Le <xref:System.Runtime.Caching> espace de noms est nouveau dans le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. Cet espace de noms rend la mise en cache est disponible à tous les [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications. Dans les versions précédentes du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], la mise en cache était disponible uniquement dans l’espace de noms <xref:System.Web> et nécessitait donc une dépendance vis-à-vis des classes ASP.NET.  
  
 Cette procédure pas à pas vous montre comment utiliser la fonctionnalité de mise en cache est disponible dans le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] en tant que partie d’un [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application. Dans la procédure pas à pas, vous mettez en cache le contenu d’un fichier texte.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un projet d’application WPF.  
  
-   Ajout d’une référence à la [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
-   Initialisation d’un cache.  
  
-   Ajout d’une entrée de cache qui contient le contenu d’un fichier texte.  
  
-   En fournissant une stratégie d’éviction de l’entrée de cache.  
  
-   Analyse le chemin d’accès du fichier mis en cache et l’informant de l’instance de cache des modifications apportées à l’élément analysé.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Un fichier texte qui contient une petite quantité de texte. (Vous afficherez le contenu du fichier texte dans une boîte de message.) Le code illustré dans la procédure pas à pas suppose que vous travaillez avec le fichier suivant :  
  
     `c:\cache\cacheText.txt`  
  
     Toutefois, vous pouvez utiliser n’importe quel fichier texte et apporter des modifications mineures au code dans cette procédure pas à pas.  
  
## <a name="creating-a-wpf-application-project"></a>Création d’un projet d’Application WPF  
 Vous commencerez par créer un projet d’application WPF.  
  
#### <a name="to-create-a-wpf-application"></a>Pour créer une application WPF  
  
1.  Démarrez [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
2.  Dans le **fichier** menu, cliquez sur **nouveau**, puis cliquez sur **nouveau projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
3.  Sous **modèles installés**, sélectionnez le langage de programmation que vous souhaitez utiliser (**Visual Basic** ou **Visual C#**).  
  
4.  Dans le **nouveau projet** boîte de dialogue, sélectionnez **Application WPF**.  
  
    > [!NOTE]
    >  Si vous ne voyez pas le **Application WPF** modèle, assurez-vous que vous ciblez une version de la [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] qui prend en charge WPF. Dans le **nouveau projet** boîte de dialogue, sélectionnez [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] dans la liste.  
  
5.  Dans le **nom** texte, entrez un nom pour votre projet. Par exemple, vous pouvez entrer **WPFCaching**.  
  
6.  Sélectionnez le **créer le répertoire pour la solution** case à cocher.  
  
7.  Cliquez sur **OK**.  
  
     Le Concepteur WPF s’ouvre dans **conception** afficher et affiche le fichier MainWindow.xaml. [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]crée le **mon projet** dossier, le fichier Application.xaml et le fichier MainWindow.xaml.  
  
## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>Ciblage du .NET Framework et l’ajout d’une référence aux assemblys de mise en cache  
 Par défaut, les applications WPF ciblent le [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]. Pour utiliser le <xref:System.Runtime.Caching> espace de noms dans une application WPF, l’application doit cibler le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (pas le [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) et doit inclure une référence à l’espace de noms.  
  
 Par conséquent, l’étape suivante consiste à modifier la cible du .NET Framework et ajoutez une référence à la <xref:System.Runtime.Caching> espace de noms.  
  
> [!NOTE]
>  La procédure de modification de la cible du .NET Framework est différente dans un projet Visual Basic et dans un projet Visual c#.  
  
#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Pour modifier la cible du .NET Framework en Visual Basic  
  
1.  Dans **l’Explorateur de Solutions**, cliquez sur le nom du projet, puis cliquez sur **propriétés**.  
  
     La fenêtre Propriétés de l’application s’affiche.  
  
2.  Cliquez sur l’onglet **Compiler**.  
  
3.  Au bas de la fenêtre, cliquez sur **Options avancées de compilation...** .  
  
     Le **paramètres avancés du compilateur** boîte de dialogue s’affiche.  
  
4.  Dans le **framework cible (toutes les configurations)** liste, sélectionnez [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Ne sélectionnez pas [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)  
  
5.  Cliquez sur **OK**.  
  
     Le **modification du Framework cible** boîte de dialogue s’affiche.  
  
6.  Dans le **modification du Framework cible** boîte de dialogue, cliquez sur **Oui**.  
  
     Le projet est fermé et puis rouvert.  
  
7.  Ajoutez une référence à l’assembly de mise en cache en suivant ces étapes :  
  
    1.  Dans **l’Explorateur de solutions**, cliquez sur le nom du projet, puis sur **ajouter une référence**.  
  
    2.  Sélectionnez le **.NET** onglet, sélectionnez `System.Runtime.Caching`, puis cliquez sur **OK**.  
  
#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>Pour modifier la cible de .NET Framework dans un projet Visual c#  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le nom du projet, puis sur **propriétés**.  
  
     La fenêtre Propriétés de l’application s’affiche.  
  
2.  Cliquez sur l’onglet **Application** .  
  
3.  Dans le **framework cible** liste, sélectionnez [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Ne sélectionnez pas **.NET Framework 4 Client Profile**.)  
  
4.  Ajoutez une référence à l’assembly de mise en cache en suivant ces étapes :  
  
    1.  Cliquez sur le **références** dossier, puis cliquez sur **ajouter une référence**.  
  
    2.  Sélectionnez le **.NET** onglet, sélectionnez `System.Runtime.Caching`, puis cliquez sur **OK**.  
  
## <a name="adding-a-button-to-the-wpf-window"></a>Ajout d’un bouton dans la fenêtre WPF  
 Ensuite, vous ajoutez un contrôle bouton et créer un gestionnaire d’événements du bouton `Click` événement. Ultérieurement, vous allez ajouter de code afin que lorsque vous cliquez sur le bouton, le contenu du fichier texte est mis en cache et affiché.  
  
#### <a name="to-add-a-button-control"></a>Pour ajouter un contrôle de bouton  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur le fichier MainWindow.xaml pour l’ouvrir.  
  
2.  À partir de la **boîte à outils**, sous **des contrôles WPF communs**, faites glisser un `Button` le contrôle à la `MainWindow` fenêtre.  
  
3.  Dans le **propriétés** , configurez la `Content` propriété de la `Button` le contrôle à **extraire du Cache**.  
  
## <a name="initializing-the-cache-and-caching-an-entry"></a>L’initialisation du Cache et la mise en cache d’une entrée  
 Ensuite, vous ajouterez le code pour effectuer les tâches suivantes :  
  
-   Créez une instance de la classe de cache, c'est-à-dire instancier un nouvel <xref:System.Runtime.Caching.MemoryCache> objet.  
  
-   Spécifiez que le cache utilise un <xref:System.Runtime.Caching.HostFileChangeMonitor> objet à surveiller les modifications dans le fichier texte.  
  
-   Lire le fichier texte et son contenu en cache comme une entrée de cache.  
  
-   Afficher le contenu du fichier texte mis en cache.  
  
#### <a name="to-create-the-cache-object"></a>Pour créer l’objet de cache  
  
1.  Double-cliquez sur le bouton que vous venez d’ajouter pour créer un gestionnaire d’événements dans le fichier MainWindow.xaml.cs ou MainWindow.Xaml.vb.  
  
2.  En haut du fichier (avant la déclaration de classe), ajoutez le code suivant `Imports` (Visual Basic) ou `using` instructions (c#) :  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  Dans le Gestionnaire d’événements, ajoutez le code suivant pour instancier l’objet de cache :  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     Le <xref:System.Runtime.Caching.ObjectCache> est une classe intégrée qui fournit un cache d’objets en mémoire.  
  
4.  Ajoutez le code suivant pour lire le contenu d’une entrée de cache nommé `filecontents`:  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  Ajoutez le code suivant pour vérifier si l’entrée de cache nommé `filecontents` existe :  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     Si l’entrée de cache spécifiée n’existe pas, vous devez lire le fichier texte et ajouter une entrée du cache dans le cache.  
  
6.  Dans le `if/then` bloquer, ajoutez le code suivant pour créer un nouveau <xref:System.Runtime.Caching.CacheItemPolicy> objet qui spécifie que l’entrée de cache expire au bout de 10 secondes.  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     Si aucune information d’éviction ou d’expiration n’est fournie, la valeur par défaut est <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, ce qui signifie que les entrées du cache n’expirent jamais en fonction uniquement sur une heure absolue. Au lieu de cela, les entrées de cache expirent uniquement en cas de sollicitation de la mémoire. Comme meilleure pratique, vous devez toujours explicitement fournir absolu ou une date d’expiration de la finition.  
  
7.  À l’intérieur de la `if/then` bloquer et après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour créer une collection pour les chemins d’accès de fichier que vous voulez surveiller et pour ajouter le chemin d’accès du fichier texte à la collection :  
  
    ```vb  
    Dim filePaths As New List(Of String)()  
    filePaths.Add("c:\cache\cacheText.txt")  
    ```  
  
    ```csharp  
    List<string> filePaths = new List<string>();  
    filePaths.Add("c:\\cache\\cacheText.txt");  
    ```  
  
    > [!NOTE]
    >  Si le fichier texte que vous souhaitez utiliser n’est pas `c:\cache\cacheText.txt`, spécifiez le chemin d’accès du fichier texte que vous souhaitez utiliser.  
  
8.  Après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour ajouter un nouveau <xref:System.Runtime.Caching.HostFileChangeMonitor> analyse de l’objet à la collection de modification pour l’entrée de cache :  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     Le <xref:System.Runtime.Caching.HostFileChangeMonitor> objet surveille le chemin d’accès du fichier texte et indique au cache si les modifications se produisent. Dans cet exemple, l’entrée de cache expire si le contenu du fichier change.  
  
9. Selon le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour lire le contenu du fichier texte :  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     L’horodatage de la date et l’heure est ajouté afin que vous ne pourrez pas voir lorsque l’entrée de cache expire.  
  
10. Après le code que vous avez ajouté à l’étape précédente, ajoutez le code suivant pour insérer le contenu du fichier dans l’objet du cache comme un <xref:System.Runtime.Caching.CacheItem> instance :  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     Vous spécifiez des informations sur le mode de suppression de l’entrée de cache en passant le <xref:System.Runtime.Caching.CacheItemPolicy> objet que vous avez créé précédemment en tant que paramètre.  
  
11. Après le `if/then` bloquer, ajoutez le code suivant pour afficher le contenu du fichier mis en cache dans une boîte de message :  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. Dans le **générer** menu, cliquez sur **générer WPFCaching** pour générer votre projet.  
  
## <a name="testing-caching-in-the-wpf-application"></a>Test de la mise en cache dans l’Application WPF  
 Vous pouvez maintenant tester l’application.  
  
#### <a name="to-test-caching-in-the-wpf-application"></a>Pour tester la mise en cache dans l’application WPF  
  
1.  Appuyez sur CTRL+F5 pour exécuter l'application.  
  
     La `MainWindow` fenêtre s’affiche.  
  
2.  Cliquez sur **obtenir Cache**.  
  
     Le contenu mis en cache à partir du fichier texte est affiché dans une boîte de message. Notez que l’horodatage du fichier.  
  
3.  Fermez la boîte de message, puis **extraire du Cache** nouveau**.**  
  
     L’horodatage reste inchangé. Cela indique que le contenu mis en cache s’affiche.  
  
4.  Attendez au moins 10 secondes, puis cliquez sur **extraire du Cache** à nouveau.  
  
     Cette fois-ci, un nouvel horodatage s’affiche. Cela indique que la stratégie de laisser l’entrée de cache expire et que le nouveau contenu mis en cache s’affiche.  
  
5.  Dans un éditeur de texte, ouvrez le fichier texte que vous avez créé. N’apportez pas encore de modifications.  
  
6.  Fermez la boîte de message, puis **extraire du Cache** nouveau**.**  
  
     Notez l’horodatage à nouveau.  
  
7.  Apportez une modification dans le fichier texte, puis enregistrez le fichier.  
  
8.  Fermez la boîte de message, puis **extraire du Cache** à nouveau.  
  
     Cette boîte de message contient le contenu mis à jour à partir du fichier texte et un nouveau horodatage. Cela indique que l’Analyseur de modification du fichier hôte supprimé l’entrée de cache immédiatement lorsque vous avez modifié le fichier, même si le délai d’expiration absolue n’a pas expiré.  
  
    > [!NOTE]
    >  Vous pouvez augmenter le temps d’éviction à 20 secondes ou plus pour permettre plus de temps pour vous permettre d’apporter une modification dans le fichier.  
  
## <a name="code-example"></a>Exemple de code  
 Après avoir terminé cette procédure pas à pas, le code pour le projet que vous avez créée ressemblera à l’exemple suivant.  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.Caching.MemoryCache>  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching>  
 [Mise en cache dans les applications .NET Framework](../../../../docs/framework/performance/caching-in-net-framework-applications.md)
