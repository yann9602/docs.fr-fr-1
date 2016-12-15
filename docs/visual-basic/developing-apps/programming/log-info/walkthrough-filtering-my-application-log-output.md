---
title: "Proc&#233;dure pas &#224; pas&#160;: filtrage de la sortie de My.Application.Log (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Log (objet), filtrage de la sortie"
  - "My.Application.Log (objet), filtrage de la sortie"
  - "journaux des événements application, le filtrage de sortie"
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Proc&#233;dure pas &#224; pas&#160;: filtrage de la sortie de My.Application.Log (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cette procédure pas à pas montre comment modifier le filtrage de journal par défaut le `My.Application.Log` objet, pour contrôler les informations passées à partir de la `Log` objet aux écouteurs et celles qui sont écrites par les écouteurs. Vous pouvez modifier le comportement de journalisation même après la création de l’application, car les informations de configuration sont stockées dans le fichier de configuration de l’application.  
  
## <a name="getting-started"></a>Prise en main  
 Chaque message qui `My.Application.Log` écritures a un niveau de gravité associé, les mécanismes de filtrage utilisent pour contrôler la sortie de journal. Cet exemple d’application utilise `My.Application.Log` pour écrire plusieurs méthodes d’enregistrer des messages avec différents niveaux de gravité.  
  
#### <a name="to-build-the-sample-application"></a>Pour générer l’exemple d’application  
  
1.  Ouvrez une nouvelle [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projet d’Application Windows.  
  
2.  Ajoutez un bouton nommé Button1 à Form1.  
  
3.  Dans la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements pour Button1, ajoutez le code suivant :  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-filtering-my-application-log-output_1.vb)]  
  
4.  Exécutez l’application dans le débogueur.  
  
5.  Appuyez sur **Button1**.  
  
     L’application écrit les informations suivantes au fichier de sortie et le journal de débogage de l’application.  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  Fermez l'application.  
  
     Pour plus d’informations sur la façon d’afficher la fenêtre de sortie de débogage de l’application, consultez [fenêtre sortie](/visual-studio/ide/reference/output-window). Pour plus d’informations sur l’emplacement du fichier journal de l’application, consultez la page [procédure pas à pas : Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
    > [!NOTE]
    >  Par défaut, l’application vide la sortie du fichier journal lorsque l’application se ferme.  
  
     Dans l’exemple ci-dessus, le deuxième appel à la <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> méthode et l’appel à la <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> méthode génère la sortie de journal, lors du premier et dernier appels à la `WriteEntry` n’est pas le cas de méthode. C’est parce que les niveaux de gravité de `WriteEntry` et `WriteException` sont « Informations » et « Erreur », qui sont autorisées par le `My.Application.Log` l’objet filtrage de journal par défaut. Toutefois, les événements avec les niveaux de gravité « Démarrage » et « Stop » ne peuvent pas produire la sortie de journal.  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a>Filtrage de tous les écouteurs de My.Application.Log  
 Le `My.Application.Log` object utilise un <xref:System.Diagnostics.SourceSwitch> nommé `DefaultSwitch` pour contrôler les messages qu’il passe de le `WriteEntry` et `WriteException` méthodes aux écouteurs de journalisation. Vous pouvez configurer `DefaultSwitch` dans le fichier de configuration de l’application en définissant sa valeur à l’un de le <xref:System.Diagnostics.SourceLevels> valeurs d’énumération. Par défaut, sa valeur est « Information ».  
  
 Ce tableau indique le niveau de gravité requis pour le journal écrire un message dans les écouteurs, étant donné que `DefaultSwitch` paramètre.  
  
|||  
|-|-|  
|Valeur DefaultSwitch|Gravité du message requise pour la sortie|  
|`Critical`|`Critical`|  
|`Error`|`Critical` ou `Error`|  
|`Warning`|`Critical`, `Error` ou `Warning`|  
|`Information`|`Critical`, `Error`, `Warning` ou `Information`|  
|`Verbose`|`Critical`, `Error`, `Warning`, `Information` ou `Verbose`|  
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, `Resume` ou `Transfer`|  
|`All`|Tous les messages sont autorisés.|  
|`Off`|Tous les messages sont bloqués.|  
  
> [!NOTE]
>  Le `WriteEntry` et `WriteException` les méthodes ont une surcharge qui ne spécifie pas un niveau de gravité. Le niveau de gravité implicite de la `WriteEntry` surcharge est « Information » et le niveau de gravité implicite de la `WriteException` surcharge est « Erreur ».  
  
 Ce tableau explique la sortie de journal indiquée dans l’exemple précédent : avec la valeur par défaut `DefaultSwitch` définition de « Information », seul le deuxième appel à la `WriteEntry` méthode et l’appel à la `WriteException` sortie de journal produisent la méthode.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Pour consigner les événements de suivi d’activité uniquement  
  
1.  Avec le bouton droit app.config dans le **l’Explorateur de solutions** et sélectionnez **Open**.  
  
     ou  
  
     S’il n’existe pas de fichier app.config :  
  
    1.  Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.  
  
    2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.  
  
    3.  Cliquez sur **Ajouter**.  
  
2.  Recherchez la `<switches>` section, qui se trouve dans le `<system.diagnostics>` section, qui se trouve dans le niveau supérieur `<configuration>` section.  
  
3.  Recherchez l’élément qui ajoute `DefaultSwitch` à la collection de commutateurs. Il doit ressembler à cet élément :  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  Modifiez la valeur de la `value` l’attribut « ActivityTracing ».  
  
5.  Le contenu du fichier app.config doit être similaire au code XML suivant :  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="ActivityTracing" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
6.  Exécutez l’application dans le débogueur.  
  
7.  Appuyez sur **Button1**.  
  
     L’application écrit les informations suivantes au fichier de sortie et le journal de débogage de l’application :  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  Fermez l'application.  
  
9. Modifiez la valeur de la `value` attribut par « Information ».  
  
    > [!NOTE]
    >  Le `DefaultSwitch` basculer uniquement les contrôles de paramètre `My.Application.Log`. Il ne modifie pas la [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.Diagnostics.Trace?displayProperty=fullName> et <xref:System.Diagnostics.Debug?displayProperty=fullName> comportement des classes.  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Filtrage individuel des écouteurs My.Application.Log  
 L’exemple précédent montre comment modifier le filtrage pour toutes les `My.Application.Log` sortie. Cet exemple montre comment filtrer un écouteur de journalisation. Par défaut, une application a deux écouteurs qui écrivent dans la sortie de débogage de l’application et le fichier journal.  
  
 Le fichier de configuration contrôle le comportement des écouteurs de journalisation en permettant à chacun d'entre eux d’avoir un filtre, qui est similaire à un commutateur de `My.Application.Log`. Un écouteur de journalisation génère un message uniquement si la gravité est autorisée par les deux le journal `DefaultSwitch` et filtre de l’écouteur journal.  
  
 Cet exemple montre comment configurer le filtrage d’un nouvel écouteur de débogage et l’ajouter à la `Log` objet. L’écouteur de débogage par défaut doit être supprimé de la `Log` de l’objet, il est clair que les messages de débogage proviennent le nouvel écouteur de débogage.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Pour consigner uniquement les événements de suivi d’activité  
  
1.  Avec le bouton droit app.config dans le **l’Explorateur de solutions** et choisissez **Open**.  
  
     ou  
  
     S’il n’existe pas de fichier app.config :  
  
    1.  Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.  
  
    2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.  
  
    3.  Cliquez sur **Ajouter**.  
  
2.  Avec le bouton droit app.config dans **l’Explorateur de solutions**. Choisissez **Open**.  
  
3.  Recherchez la `<listeners>` section, dans la `<source>` section avec le `name` attribut « DefaultSource », situé dans le `<sources>` section. Le `<sources>` section est sous le `<system.diagnostics>` section, dans le niveau supérieur `<configuration>` section.  
  
4.  Ajoutez cet élément à la `<listeners>` section :  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  Recherchez la section `<sharedListeners>` dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.  
  
6.  Ajoutez cet élément à cette section `<sharedListeners>` :  
  
    ```xml  
    <add name="NewDefault"   
         type="System.Diagnostics.DefaultTraceListener,   
               System, Version=2.0.0.0, Culture=neutral,   
               PublicKeyToken=b77a5c561934e089,   
               processorArchitecture=MSIL">  
        <filter type="System.Diagnostics.EventTypeFilter"   
                initializeData="Error" />  
    </add>  
    ```  
  
     Le <xref:System.Diagnostics.EventTypeFilter> filtre prend l’une de la <xref:System.Diagnostics.SourceLevels> valeurs d’énumération en tant que son `initializeData` attribut.  
  
7.  Le contenu du fichier app.config doit être similaire au code XML suivant :  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Remove the default debug listener. -->  
              <remove name="Default"/>  
              <!-- Add a filterable debug listener. -->  
              <add name="NewDefault"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="Information" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
          <add name="NewDefault"   
               type="System.Diagnostics.DefaultTraceListener,   
                     System, Version=2.0.0.0, Culture=neutral,   
                     PublicKeyToken=b77a5c561934e089,   
                     processorArchitecture=MSIL">  
            <filter type="System.Diagnostics.EventTypeFilter"   
                    initializeData="Error" />  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
8.  Exécutez l’application dans le débogueur.  
  
9. Appuyez sur **Button1**.  
  
     L’application écrit les informations suivantes au fichier journal de l’application :  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     L’application écrit moins d’informations à la sortie de débogage de l’application en raison du filtrage plus restrictif.  
  
     `Default Error   2   Error`  
  
10. Fermez l'application.  
  
 Pour plus d’informations sur la modification des paramètres de journal après le déploiement, consultez la page [utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Détermination où des informations My.application.log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)   
 [Procédure pas à pas : Modifier l’emplacement des informations My.application.log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)   
 [Procédure pas à pas : Création d’écouteurs de journalisation personnalisés](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)   
 [Comment : écrire des Messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)   
 [Commutateurs de traçage](../Topic/Trace%20Switches.md)   
 [Informations de journalisation de l’Application](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)