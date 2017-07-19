---
title: "Proc&#233;dure pas &#224; pas&#160;: mise en cache de donn&#233;es d&#39;application dans une application WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mise en cache (.NET Framework)"
  - "mise en cache (WPF)"
  - "procédures pas à pas (WPF), mettre en cache"
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# Proc&#233;dure pas &#224; pas&#160;: mise en cache de donn&#233;es d&#39;application dans une application WPF
La mise en cache vous permet de stocker des données en mémoire pour y accéder rapidement.  Lors d'un nouvel accès aux données, les applications peuvent les obtenir du cache au lieu de les extraire de la source d'origine.  Cela peut améliorer le niveau de performance et l'extensibilité.  En outre, la mise en cache rend les données disponibles lorsque la source de données est temporairement indisponible.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fournit des classes qui vous permettent d'utiliser la mise en cache dans les applications de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] .  Ces classes figurent dans l'espace de noms d' <xref:System.Runtime.Caching> .  
  
> [!NOTE]
>  L'espace de noms <xref:System.Runtime.Caching> est une nouveauté de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  Cet espace de noms rend la mise en cache disponible pour toutes les applications [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  Dans les versions précédentes du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], la mise en cache était disponible uniquement dans l'espace de noms <xref:System.Web> et nécessitait donc une dépendance sur les classes ASP.NET.  
  
 Cette procédure pas à pas vous indique comment utiliser les fonctionnalités de mise en cache qui sont disponibles dans [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dans le cadre d'une application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Dans la procédure pas à pas, vous mettez en cache le contenu d'un fichier texte.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet d'application WPF.  
  
-   Ajout d'une référence à [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
-   Initialisation d'un cache.  
  
-   Ajout d'une entrée de cache qui abrite le contenu d'un fichier texte.  
  
-   Fourniture d'une stratégie d'éviction pour l'entrée de cache.  
  
-   Analyse du chemin d'accès du fichier mis en cache et notification auprès de l'instance de cache des modifications apportées à l'élément surveillé.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Fichier texte contenant une petite quantité de texte.  \(Le contenu du fichier texte s'affiche dans une boîte de message.\) Le code illustré dans la procédure pas à pas suppose que vous utilisez le fichier suivant :  
  
     `c:\cache\cacheText.txt`  
  
     Toutefois, vous pouvez utiliser n'importe quel fichier texte et apporter de petites modifications au code dans cette procédure pas à pas.  
  
## Création d'un projet d'application WPF  
 Vous allez commencer par créer un projet d'application WPF.  
  
#### Pour créer une application WPF  
  
1.  Démarrez [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Nouveau projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Sous **Modèles installés**, sélectionnez le langage de programmation que vous souhaitez utiliser \(**Visual Basic** ou **Visual C\#**\).  
  
4.  Dans la boîte de dialogue **Nouveau projet**, sélectionnez **Application WPF**.  
  
    > [!NOTE]
    >  Si vous ne voyez pas le modèle **Application WPF**, assurez\-vous que vous ciblez une version du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] qui prend en charge WPF.  Dans la boîte de dialogue **Nouveau projet**, sélectionnez [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] dans la liste.  
  
5.  Dans la zone de texte **Nom**, entrez un nom pour votre projet.  Par exemple, vous pouvez entrer WPFCaching.  
  
6.  Activez la case à cocher **Créer le répertoire pour la solution**.  
  
7.  Cliquez sur **OK**.  
  
     Le Concepteur WPF s'ouvre en mode **Création** et affiche le fichier MainWindow.xaml.  [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] crée le dossier **My Project**, le fichier Application.xaml et le fichier MainWindow.xaml.  
  
## Ciblage du .NET Framework et ajout d'une référence aux assemblys de mise en cache  
 Par défaut, les applications WPF ciblent le [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].  Pour utiliser l'espace de noms <xref:System.Runtime.Caching> dans une application WPF, l'application doit cibler le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] \(pas le [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]\) et doit comprendre une référence à l'espace de noms.  
  
 Par conséquent, l'étape suivante consiste à modifier la cible du .NET Framework et à ajouter une référence à l'espace de noms <xref:System.Runtime.Caching>.  
  
> [!NOTE]
>  La procédure de modification de la cible du .NET Framework est différente dans un projet Visual Basic et dans un projet Visual C\#.  
  
#### Pour modifier la cible du .NET Framework dans Visual Basic  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Propriétés**.  
  
     La fenêtre Propriétés de l'application s'affiche.  
  
2.  Cliquez sur l'onglet **Compiler**.  
  
3.  Dans la partie inférieure de la fenêtre, cliquez sur **Options avancées de compilation**.  
  
     La boîte de dialogue **Paramètres avancés du compilateur** s'affiche.  
  
4.  dans la liste de **Framework cible \(toutes les configurations\)** , sélectionnez [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  \(Ne sélectionnez pas [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].\)  
  
5.  Cliquez sur **OK**.  
  
     La boîte de dialogue **Modification du Framework cible** s'affiche.  
  
6.  Dans la boîte de dialogue **Modification du Framework cible**, cliquez sur **Oui**.  
  
     Le projet est fermé puis rouvert.  
  
7.  Ajoutez une référence à l'assembly de mise en cache en suivant ces étapes :  
  
    1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Ajouter une référence**.  
  
    2.  Sélectionnez l'onglet **.NET**, sélectionnez `System.Runtime.Caching`, puis cliquez sur **OK**.  
  
#### Pour modifier la cible du .NET Framework dans un projet Visual C\#  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet puis cliquez sur **Propriétés**.  
  
     La fenêtre Propriétés de l'application s'affiche.  
  
2.  Cliquez sur l'onglet **Application**.  
  
3.  Dans la liste **Framework cible**, sélectionnez [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  \(Ne sélectionnez pas **.NET Framework 4 Client Profile**.\)  
  
4.  Ajoutez une référence à l'assembly de mise en cache en suivant ces étapes :  
  
    1.  Cliquez avec le bouton droit sur le dossier **Références**, puis cliquez sur **Ajouter une référence**.  
  
    2.  Sélectionnez l'onglet **.NET**, sélectionnez `System.Runtime.Caching`, puis cliquez sur **OK**.  
  
## Ajout d'un bouton dans la fenêtre WPF  
 Ensuite, vous allez ajouter un contrôle bouton et créer un gestionnaire d'événements pour l'événement `Click` du bouton.  Ultérieurement, vous ajouterez du code de sorte que lorsque vous cliquez sur le bouton, le contenu du fichier texte est mis en cache et affiché.  
  
#### Pour ajouter un contrôle bouton  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur le fichier MainWindow.xaml pour l'ouvrir.  
  
2.  Dans la **Boîte à outils**, sous **Contrôles WPF communs**, faites glisser un contrôle `Button` dans la fenêtre `MainWindow`.  
  
3.  Dans la fenêtre **Propriétés**, définissez la propriété `Content` du contrôle `Button` sur Extraire du cache.  
  
## Initialisation du cache et mise en cache d'une entrée  
 Vous allez ensuite ajouter le code pour effectuer les tâches suivantes :  
  
-   Créer une instance de la classe de cache, c'est\-à\-dire instancier un nouvel objet <xref:System.Runtime.Caching.MemoryCache>.  
  
-   Spécifier que le cache utilise un objet <xref:System.Runtime.Caching.HostFileChangeMonitor> pour surveiller les modifications apportées dans le fichier texte.  
  
-   Lire le fichier texte et mettre en cache son contenu en tant qu'entrée de cache.  
  
-   Afficher le contenu du fichier texte mis en cache.  
  
#### Pour créer l'objet de cache  
  
1.  Double\-cliquez sur le bouton que vous venez d'ajouter afin de créer un gestionnaire d'événements dans le fichier MainWindow.xaml.cs ou MainWindow.Xaml.vb.  
  
2.  Au début du fichier \(avant la déclaration de classe\), ajoutez les instructions `Imports` \(Visual Basic\) ou `using` \(C\#\) suivantes.  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  Dans le gestionnaire d'événements, ajoutez le code suivant pour instancier l'objet de cache :  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     La classe <xref:System.Runtime.Caching.ObjectCache> est une classe intégrée qui fournit un cache d'objets en mémoire.  
  
4.  Ajoutez le code suivant pour lire le contenu d'une entrée de cache nommée `filecontents` :  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  Ajoutez le code suivant pour vérifier si l'entrée de cache nommée `filecontents` existe :  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     Si l'entrée de cache spécifiée n'existe pas, vous devez lire le fichier texte et l'ajouter au cache en tant qu'entrée de cache.  
  
6.  Dans le bloc `if/then`, ajoutez le code suivant pour créer un objet <xref:System.Runtime.Caching.CacheItemPolicy> qui spécifie que l'entrée de cache expire après 10 secondes.  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     Si aucune information relative à l'éviction ou à l'expiration n'est fournie, la valeur par défaut est <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, ce qui signifie que les entrées de cache n'expirent jamais seulement en fonction d'une heure absolue.  Au lieu de cela, les entrées de cache expirent uniquement en cas de sollicitation de la mémoire.  Il est recommandé de fournir explicitement une heure d'expiration absolue ou décalée.  
  
7.  À l'intérieur du bloc `if/then` et à la suite du code que vous avez ajouté au cours de l'étape précédente, ajoutez le code suivant pour créer une collection pour les chemins d'accès aux fichiers que vous souhaitez surveiller et pour ajouter le chemin d'accès du fichier texte à la collection :  
  
    ```vb  
    Dim filePaths As New List(Of String)()  
    filePaths.Add("c:\cache\cacheText.txt")  
    ```  
  
    ```csharp  
    List<string> filePaths = new List<string>();  
    filePaths.Add("c:\\cache\\cacheText.txt");  
    ```  
  
    > [!NOTE]
    >  Si le fichier texte que vous souhaitez utiliser n'est pas `c:\cache\cacheText.txt`, spécifiez le chemin d'accès du fichier texte que vous souhaitez utiliser.  
  
8.  À la suite du code que vous avez ajouté au cours de l'étape précédente, ajoutez le code suivant pour ajouter un objet <xref:System.Runtime.Caching.HostFileChangeMonitor> à la collection d'analyseurs de modification pour l'entrée de cache.  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     L'objet <xref:System.Runtime.Caching.HostFileChangeMonitor> surveille le chemin d'accès du fichier texte et notifie le cache en cas de modification.  Dans cet exemple, l'entrée de cache expire si le contenu du fichier change.  
  
9. À la suite du code que vous avez ajouté au cours de l'étape précédente, ajoutez le code suivant pour lire le contenu du fichier texte :  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     L'horodatage de la date et de l'heure est ajouté afin que vous puissiez voir quand l'entrée du cache expire.  
  
10. À la suite du code que vous avez ajouté au cours de l'étape précédente, ajoutez le code suivant pour insérer le contenu du fichier dans l'objet de cache sous forme d'instance <xref:System.Runtime.Caching.CacheItem> :  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     Vous spécifiez les informations relatives à l'expulsion de l'entrée de cache en passant l'objet <xref:System.Runtime.Caching.CacheItemPolicy> juste créé comme paramètre.  
  
11. Après le bloc `if/then`, ajoutez le code suivant pour afficher le contenu du fichier mis en cache dans une boîte de message :  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. Dans le menu **Générer**, cliquez sur **Générer WPFCaching** pour générer votre projet.  
  
## Test de la mise en cache dans l'application WPF  
 Vous pouvez maintenant tester l'application.  
  
#### Pour tester la mise en cache dans l'application WPF  
  
1.  Appuyez sur CTRL\+F5 pour exécuter l'application.  
  
     La fenêtre `MainWindow` s'affiche.  
  
2.  Cliquez sur **Extraire du cache**.  
  
     Le contenu mis en cache du fichier texte s'affiche dans une boîte de message.  Notez l'horodatage du fichier.  
  
3.  Fermez la boîte de message, puis cliquez à nouveau sur **Extraire du cache** **.**  
  
     L'horodatage reste inchangé.  Cela indique le contenu mis en cache est affiché.  
  
4.  Attendez au moins 10 secondes, puis cliquez à nouveau sur **Extraire du cache**.  
  
     Cette fois\-ci, un nouvel horodatage s'affiche.  Cela indique que la stratégie a permis à l'entrée de cache d'expirer et que le nouveau contenu mis en cache s'affiche.  
  
5.  Dans un éditeur de texte, ouvrez le fichier texte que vous avez créé.  N'apportez pas encore de modifications.  
  
6.  Fermez la boîte de message, puis cliquez à nouveau sur **Extraire du cache** **.**  
  
     Notez à nouveau l'horodatage.  
  
7.  Apportez une modification au fichier texte, puis enregistrez le fichier.  
  
8.  Fermez la boîte de message, puis cliquez à nouveau sur **Extraire du cache**.  
  
     Cette boîte de message contient le contenu mis à jour du fichier texte et un nouvel horodatage.  Cela indique que l'analyseur de modification de fichier d'hôte a procédé immédiatement à l'éviction de l'entrée du cache lorsque vous avez modifié le fichier, bien que le délai d'expiration absolue n'ait pas expiré.  
  
    > [!NOTE]
    >  Vous pouvez augmenter le temps d'éviction à 20 secondes ou plus pour disposer de plus de temps pour modifier le fichier.  
  
## Exemple de code  
 Une fois cette procédure pas à pas terminée, le code du projet que vous avez créé se présentera comme dans l'exemple suivant.  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## Voir aussi  
 <xref:System.Runtime.Caching.MemoryCache>   
 <xref:System.Runtime.Caching.ObjectCache>   
 <xref:System.Runtime.Caching>   
 [Mise en cache dans les applications .NET Framework](../../../../docs/framework/performance/caching-in-net-framework-applications.md)