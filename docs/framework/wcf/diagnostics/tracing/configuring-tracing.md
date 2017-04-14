---
title: "Configuration du suivi | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "suivi (WCF)"
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
caps.latest.revision: 53
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 53
---
# Configuration du suivi
Cette rubrique décrit comment activer le suivi, configurer des sources de suivi pour émettre des suivis et définir des niveaux de suivi, définir le suivi et la propagation d'activité afin de prendre en charge la corrélation de suivi de bout en bout, et définir des écouteurs de suivi pour accéder aux suivis.  
  
 Pour obtenir les recommandations relatives aux paramètres de suivi dans un environnement de production ou de débogage, consultez [Paramètres recommandés pour le suivi et l'enregistrement des messages](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
>  Sur Windows 8 vous devez exécuter votre application avec élévation de privilèges \(Exécuter en tant qu'administrateur\) pour lui permettre de générer des journaux de suivi.  
  
## Activation du suivi  
 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] génère les données suivantes pour le suivi de diagnostic :  
  
-   Suivis des jalons de processus dans l'ensemble des composants des applications, tels que les appels d'opération, les exceptions de code, les avertissements et d'autres événements de traitement significatifs.  
  
-   Événements d'erreur Windows en cas de dysfonctionnement de la fonctionnalité de suivi.Consultez [Journalisation des événements](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 Le suivi [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] est construit sur <xref:System.Diagnostics>.Pour utiliser le traçage, vous devez définir des sources de trace dans le fichier de configuration ou dans le code.[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] définit une source de suivi pour chaque assembly [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].La source de suivi `System.ServiceModel` est la source de suivi [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] la plus générale ; elle enregistre des jalons de traitement dans la pile de communication [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], de l'entrée\/sortie de transport à l'entrée\/sortie de code utilisateur.La source de suivi `System.ServiceModel.MessageLogging` enregistre tous les messages qui circulent dans le système.  
  
 Le suivi est désactivé par défaut.Pour activer le suivi, vous devez créer un écouteur de suivi et définir un niveau de suivi autre que « Désactivé » pour la source de suivi sélectionnée dans la configuration ; autrement, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ne génère pas de suivi.Si vous ne spécifiez pas d'écouteur, le suivi est automatiquement désactivé.Si un écouteur est défini mais qu'aucun niveau n'est spécifié, le niveau a la valeur « Désactivé » par défaut, ce qui signifie qu'aucun suivi n'est émis.  
  
 Si vous utilisez des points d'extensibilité [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], tels que des demandeurs d'opérations personnalisés, vous devez émettre vos propres suivis.En effet, si vous implémentez un point d'extensibilité, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] n'est plus en mesure d'émettre les suivis standard dans le chemin d'accès par défaut.Si vous n'implémentez par la prise en charge du suivi manuel à l'aide de l'émission de suivis, les suivis peuvent ne pas s'afficher comme prévu.  
  
 Vous pouvez configurer le suivi en modifiant le fichier de configuration de l'application : Web.config pour les applications hébergées sur le Web, ou Appname.exe.config pour les applications auto\-hébergées.Vous trouverez ci\-dessous un exemple de ce type de modification :Pour plus d'informations sur ces paramètres, consultez la section « Configuration d'écouteurs de suivi pour consommer des suivis ».  
  
```  
<configuration>  
   <system.diagnostics>  
      <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
>  Pour modifier le fichier de configuration d'un projet de service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dans [!INCLUDE[vs_current_short](../../../../../includes/vs-current-short-md.md)], cliquez avec le bouton droit sur le fichier de configuration de l'application \(Web.config pour les applications hébergées sur le Web, ou Appname.exe.config pour les applications auto\-hébergées dans l'**Explorateur de solutions**\).Choisissez ensuite l'élément de menu contextuel **Modifier la configuration WCF**.Cela lance [Outil Éditeur de configuration \(SvcConfigEditor.exe\)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), qui vous permet de modifier les paramètres de configuration des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] à l'aide d'une interface utilisateur graphique.  
  
## Configuration de sources de suivi de façon à émettre des suivis  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] définit une source de suivi pour chaque assembly.Les écouteurs définis pour cette source accèdent aux suivis générés dans un assembly.Les sources de suivi suivantes sont définies :  
  
-   System.ServiceModel : enregistre toutes les phases de traitement [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], chaque lecture de la configuration, chaque message traité dans le transport, le traitement de sécurité, chaque envoi d'un message dans le code utilisateur, etc.  
  
-   System.ServiceModel.MessageLogging : enregistre tous les messages qui circulent dans le système.  
  
-   System.IdentityModel.  
  
-   System.ServiceModel.Activation.  
  
-   System.IO.Log : enregistrement pour l'interface .NET Framework dans le système CLFS \(Common Log File System\).  
  
-   System.Runtime.Serialization : enregistre la lecture ou l'écriture des objets.  
  
-   CardSpace.  
  
 Vous pouvez configurer chaque source de suivi de façon à utiliser le même écouteur \(partagé\), comme indiqué dans l'exemple de configuration suivant :  
  
```  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 De plus, vous pouvez ajouter des sources de suivi définies par l'utilisateur, comme illustré par l'exemple suivant, de façon à émettre des suivis de code utilisateur :  
  
```  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />   
</system.diagnostics>  
```  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] la création de sources de suivi définies par l'utilisateur, consultez [Extending Tracing](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## Configuration d'écouteurs de suivi pour consommer des suivis  
 Au moment de l'exécution, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] fournit des données de suivi aux écouteurs qui traitent les données.[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] fournit plusieurs écouteurs prédéfinis pour <xref:System.Diagnostics>, qui diffèrent quant au format utilisé pour la sortie.Vous pouvez également ajouter des types d'écouteurs personnalisés.  
  
 Vous pouvez utiliser `add` pour indiquer les nom et type de l'écouteur de suivi à utiliser.Dans notre exemple de configuration, nous avons nommé l'écouteur `traceListener` et ajouté l'écouteur de suivi standard .NET Framework \(`System.Diagnostics.XmlWriterTraceListener`\) comme type à utiliser.Vous pouvez ajouter un nombre quelconque d'écouteurs de suivi pour chaque source.Si l'écouteur de suivi émet le suivi dans un fichier, vous devez spécifier le nom et l'emplacement du fichier de sortie dans le fichier de configuration.Pour cela, vous devez affecter à `initializeData` le nom du fichier pour cet écouteur.Si vous ne spécifiez pas de nom de fichier, un nom de fichier aléatoire est généré en fonction du type d'écouteur utilisé.Si <xref:System.Diagnostics.XmlWriterTraceListener> est utilisé, un nom de fichier sans extension est généré.Si vous implémentez un écouteur personnalisé, vous pouvez également utiliser cet attribut pour recevoir des données d'initialisation autres qu'un nom de fichier.Par exemple, vous pouvez spécifier un identificateur de base de données pour cet attribut.  
  
 Vous pouvez configurer un écouteur de suivi personnalisé pour envoyer des suivis sur le câble, par exemple à une base de données distante.En tant que responsable du déploiement d'applications, vous devez appliquer un contrôle d'accès approprié sur les journaux de suivi sur l'ordinateur distant.  
  
 Vous pouvez également configurer un écouteur de suivi par programmation.[!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Comment : créer et initialiser des écouteurs de suivi](http://go.microsoft.com/fwlink/?LinkId=94648) et [Création d'un TraceListener personnalisé](http://go.microsoft.com/fwlink/?LinkId=96239) \(pages pouvant être en anglais\)  
  
> [!CAUTION]
>  `System.Diagnostics.XmlWriterTraceListener` n'étant pas thread\-safe, la source de suivi peut verrouiller des ressources exclusivement lors de la sortie de suivis.Lorsque de nombreux threads sortent des suivis vers une source de suivi configurée pour utiliser cet écouteur, un conflit de ressource peut se produire, provoquant une dégradation significative des performances.Pour résoudre ce problème, vous devez implémenter un écouteur personnalisé thread\-safe.  
  
## Niveau de suivi  
 Le niveau de suivi est contrôlé par le paramètre `switchValue` de la source de suivi.Les niveaux de suivi disponibles sont décrits dans le tableau suivant.  
  
|Niveau de suivi|Nature des événements suivis|Contenu des événements suivis|Événements suivis|Cible utilisateur|  
|---------------------|----------------------------------|-----------------------------------|-----------------------|-----------------------|  
|Off|N\/A|N\/A|Aucun suivi n'est émis.|N\/A|  
|Critique|Événements « négatifs » : événements qui indiquent un traitement inattendu ou une condition d'erreur.||Les exceptions non prises en charge, notamment les suivantes, sont enregistrées :<br /><br /> -   OutOfMemoryException<br />-   ThreadAbortException \(le CLR appelle tout ThreadAbortExceptionHandler\)<br />-   StackOverflowException \(interception impossible\)<br />-   ConfigurationErrorsException<br />-   SEHException<br />-   Erreurs de démarrage d'application<br />-   Événements Failfast<br />-   Blocages système<br />-   Messages incohérents : suivis de messages qui provoquent l'échec de l'application.|Administrateurs<br /><br /> Développeurs d'applications|  
|Erreur|Événements « négatifs » : événements qui indiquent un traitement inattendu ou une condition d'erreur.|Un traitement inattendu s'est produit.L'application n'a pas pu effectuer une tâche comme prévu.Toutefois, l'application s'exécute encore.|Toutes les exceptions sont enregistrées.|Administradores<br /><br /> Développeurs d'applications|  
|Avertissement|Événements « négatifs » : événements qui indiquent un traitement inattendu ou une condition d'erreur.|Un problème possible s'est produit ou peut se produire, mais l'application fonctionne encore correctement.Toutefois, elle risque de ne plus fonctionner correctement.|-   L'application reçoit davantage de demandes que ses paramètres de limitation ne l'autorisent.<br />-   La file d'attente de réception est proche de sa capacité maximale configurée.<br />-   Le délai d'attente a expiré.<br />-   Les informations d'identification sont refusées.|Administradores<br /><br /> Développeurs d'applications|  
|Informations|Événements « positifs » : événements qui marquent des jalons atteints|Jalons importants et atteints relatifs à l'exécution d'application, indépendamment du fonctionnement correct de l'application.|En général, des messages d'aide au contrôle et au diagnostic de l'état système, à la mesure des performances ou au profilage sont générés.Vous pouvez utiliser ces informations pour la planification de capacité et la gestion des performances :<br /><br /> -   Des canaux sont créés.<br />-   Des écouteurs de point de terminaison sont créés.<br />-   Un message pénètre\/quitte le transport.<br />-   Un jeton de sécurité est récupéré.<br />-   Un paramètre de configuration est lu.|Administradores<br /><br /> Développeurs d'applications<br /><br /> Développeurs de produits.|  
|Verbose|Événements « positifs » : événements qui marquent des jalons atteints.|Des événements de bas niveau pour le code utilisateur et la maintenance sont émis.|En général, vous pouvez utiliser ce niveau pour le débogage ou l'optimisation d'application.<br /><br /> -   En\-tête de message compris.|Administradores<br /><br /> Développeurs d'applications<br /><br /> Développeurs de produits.|  
|ActivityTracing||Transfert d'événements entre des activités de traitement et des composants.|Ce niveau permet aux administrateurs et aux développeurs de corréler des applications dans le même domaine d'application :<br /><br /> -   Suivis des limites d'activité, par exemple démarrage\/arrêt.<br />-   Suivis pour les transferts.|Tout|  
|Tout||L'application peut fonctionner correctement.Tous les événements sont émis.|Tous les événements précédents.|Tout|  
  
 Les niveaux compris entre Verbose et Critique sont empilés les uns sur les autres, autrement dit chaque niveau de suivi inclut tous les niveaux supérieurs hormis le niveau Désactivé.Par exemple, un écouteur qui écoute au niveau Avertissement reçoit les suivis des niveaux Critique, Erreur et Avertissement.Le niveau Tout inclut les événements du niveau Verbose au niveau Critique et les événements ActivityTracing.  
  
> [!CAUTION]
>  Les niveaux Informations, Commentaires et ActivityTracing génèrent de nombreux suivis, ce qui peut avoir un impact négatif sur le débit des messages si vous avez utilisé toutes les ressources disponibles sur l'ordinateur.  
  
## Configuration du suivi d'activité et de la propagation pour la corrélation  
 La valeur `activityTracing` spécifiée pour l'attribut `switchValue` est utilisée pour activer le suivi d'activité, qui émet des suivis pour les transferts et limites d'activité dans les points de terminaison.  
  
> [!NOTE]
>  Lorsque vous utilisez certaines fonctionnalités d'extensibilité dans [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], vous pouvez obtenir un <xref:System.NullReferenceException> lorsque le suivi d'activité est activé.Pour résoudre ce problème, vérifiez le fichier de configuration de votre application et assurez\-vous que l'attribut `switchValue` de votre source de suivi n'a pas la valeur `activityTracing`.  
  
 L'attribut `propagateActivity` indique si l'activité doit être propagée vers d'autres points de terminaison qui participent à l'échange de messages.En affectant à cet attribut la valeur `true`, vous pouvez prendre des fichiers de suivi générés par deux points de terminaison quelconque et observer comment un ensemble de suivis sur un point de terminaison a été transféré vers un ensemble de suivis sur un autre point de terminaison.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] le suivi et la propagation des activités, consultez [Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Les deux valeurs booléennes `propagateActivity` et `ActivityTracing` s'appliquent à System.ServiceModel TraceSource.La valeur `ActivityTracing` s'applique également à toute source de suivi, y compris les sources [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ou définies par l'utilisateur.  
  
 Vous ne pouvez pas utiliser l'attribut `propagateActivity` avec des sources de suivi définies par l'utilisateur.Pour la propagation d'ID d'activité de code utilisateur, assurez\-vous de ne pas définir ServiceModel `ActivityTracing`, tout en ayant encore l'attribut `propagateActivity` ServiceModel défini à `true`.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)   
 [Procédure: créer et initialiser des écouteurs de suivi](http://go.microsoft.com/fwlink/?LinkId=94648)   
 [Création d'un TraceListener personnalisé](http://go.microsoft.com/fwlink/?LinkId=96239)