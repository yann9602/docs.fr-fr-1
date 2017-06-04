---
title: "How to: Use TraceSource and Filters with Trace Listeners | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "initializing trace listeners"
  - "configuration files [.NET Framework], trace listeners"
  - "app.config files, trace listeners"
  - "levels of writing trace messages"
  - "trace listeners, TraceSource class"
  - "application configuration files, trace listeners"
  - "filters, trace listeners"
  - "TraceSource class, trace listeners"
  - "trace listeners, creating"
  - "trace listeners, filters"
  - "trace listeners, initializing"
ms.assetid: 21dc2169-947d-453a-b0e2-3dac3ba0cc9f
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Use TraceSource and Filters with Trace Listeners
L'une des nouveautés du .NET Framework version 2.0 est un système de traçage amélioré.  Le principe de base reste inchangé : les messages de traçage sont envoyés par l'intermédiaire de commutateurs aux écouteurs qui transmettent les données à un support de sortie associé.  Une différence majeure de la version 2.0 est que les traces peuvent être initialisées via des instances de la classe <xref:System.Diagnostics.TraceSource>.  <xref:System.Diagnostics.TraceSource> est conçu pour fonctionner comme système de traçage amélioré et peut être utilisé à la place des méthodes statiques des anciennes classes de traçage <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug>.  Les classes <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> existent encore mais l'utilisation de la classe <xref:System.Diagnostics.TraceSource> est désormais la méthode recommandée pour le traçage.  
  
 Cette rubrique décrit l'utilisation de la classe <xref:System.Diagnostics.TraceSource> associée à un fichier de configuration de l'application.  Il est déconseillé mais néanmoins possible d'effectuer le traçage à l'aide de <xref:System.Diagnostics.TraceSource> sans utiliser de fichier de configuration.  Pour plus d'informations sur le traçage sans fichier de configuration, consultez [Comment : créer et initialiser les sources de trace](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).  
  
### Pour créer et initialiser votre source de trace  
  
1.  Pour instrumenter une application avec le traçage, la première étape consiste à créer une source de trace.  Dans les projets importants intégrant divers composants, vous pouvez créer une source de trace séparée pour chaque composant.  La méthode conseillée consiste à utiliser le nom de l'application comme nom de la source de trace.  Cela permet de distinguer plus facilement les différentes traces.  Le code suivant crée une nouvelle source de trace \(`mySource)` et appelle une méthode \(`Activity1`\) qui trace des événements.  Les messages de trace sont écrits par l'écouteur de la trace par défaut.  
  
    ```  
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
        }  
    }  
    ```  
  
### Pour créer et initialiser des filtres et des écouteurs de la trace  
  
1.  Le code de la première procédure n'identifie aucun filtre ou écouteur de la trace par programme.  Le code permet uniquement d'écrire les messages de trace dans l'écouteur de la trace par défaut.  Pour configurer des écouteurs de traces spécifiques et leurs filtres respectifs, modifiez le fichier de configuration correspondant au nom de votre application.  Dans ce fichier, vous pouvez ajouter ou supprimer un écouteur, définir les propriétés et un filtre pour un écouteur ou supprimer des écouteurs.  L'exemple de fichier de configuration suivant montre comment initialiser un écouteur de la trace de console et un écouteur de la trace du writer de texte pour la source de la trace créée dans la procédure précédente.  En plus de configurer les écouteurs de la trace, le fichier de configuration crée des filtres pour les deux écouteurs ainsi qu'un commutateur source pour la source de trace.  L'exemple illustre deux techniques pour ajouter des écouteurs de la trace : l'ajout direct de l'écouteur à la source de trace et l'ajout d'un écouteur à la collection d'écouteurs partagés suivi de l'ajout de son nom à la source de trace.  Les filtres identifiés pour les deux écouteurs sont initialisés avec des niveaux de source différents.  Par conséquent, certains messages ne sont écrits que par un seul des deux écouteurs.  
  
    ```  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"   
            switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"   
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"   
                  initializeData="Warning"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Warning"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"   
            type="System.Diagnostics.TextWriterTraceListener"   
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### Pour modifier le niveau auquel un écouteur écrit un message de trace  
  
1.  Le fichier de configuration initialise les paramètres de la source de trace lors de l'initialisation de l'application.  Pour modifier ces paramètres, vous devez modifier le fichier de configuration et redémarrer l'application ou actualiser l'application par programme à l'aide de la méthode <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=fullName>.  L'application peut modifier dynamiquement les propriétés définies par le fichier de configuration pour substituer des paramètres spécifiés par l'utilisateur.  Vous pouvez, par exemple, décider que les messages critiques seront toujours envoyés à un fichier texte, quels que soient les paramètres de configuration actuels.  
  
    ```  
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
  
                // Change the event type for which tracing occurs.  
                // The console trace listener must be specified   
                // in the configuration file. First, save the original  
                // settings from the configuration file.  
                EventTypeFilter configFilter =   
                    (EventTypeFilter)mySource.Listeners["console"].Filter;  
  
                // Then create a new event type filter that ensures   
                // critical messages will be written.  
                mySource.Listeners["console"].Filter =  
                    new EventTypeFilter(SourceLevels.Critical);  
                Activity2();  
  
                // Allow the trace source to send messages to listeners   
                // for all event types. This statement will override   
                // any settings in the configuration file.  
                mySource.Switch.Level = SourceLevels.All;  
  
                // Restore the original filter settings.  
                mySource.Listeners["console"].Filter = configFilter;  
                Activity3();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
            static void Activity2()  
            {  
                mySource.TraceEvent(TraceEventType.Critical, 3,   
                    "Critical message.");  
                mySource.TraceInformation("Informational message.");  
            }  
            static void Activity3()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 4,   
                    "Error message.");  
                mySource.TraceInformation("Informational message.");  
            }  
        }  
    }  
    ```  
  
## Voir aussi  
 <xref:System.Diagnostics.TraceSource>   
 <xref:System.Diagnostics.TextWriterTraceListener>   
 <xref:System.Diagnostics.ConsoleTraceListener>   
 <xref:System.Diagnostics.EventTypeFilter>   
 [Comment : créer et initialiser les sources de trace](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)   
 [Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md)