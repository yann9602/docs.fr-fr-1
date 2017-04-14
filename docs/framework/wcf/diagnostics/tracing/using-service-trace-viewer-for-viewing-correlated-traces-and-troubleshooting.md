---
title: "Utilisation de Service Trace Viewer pour afficher les suivis corr&#233;l&#233;s et r&#233;soudre les probl&#232;mes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 22
---
# Utilisation de Service Trace Viewer pour afficher les suivis corr&#233;l&#233;s et r&#233;soudre les probl&#232;mes
Cette rubrique décrit le format des données de suivi, leur mode de consultation, et les approches qui utilisent Service Trace Viewer pour résoudre les problèmes posés par votre application.  
  
## Utilisation de l'outil Service Trace Viewer  
 L'outil Service Trace Viewer [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] vous aide à corréler des suivis de diagnostic produits par les écouteurs [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] pour localiser l'origine d'une erreur.  L'outil vous permet de consulter, regrouper et filtrer facilement les suivis afin de pouvoir diagnostiquer, réparer et vérifier les problèmes liés aux services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].  Pour plus d'informations sur l'utilisation de cet outil, consultez [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 Cette rubrique contient des captures d'écran de suivis générés en exécutant l'exemple [Tracing and Message Logging](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) et consultés à l'aide de l'[Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  Cette rubrique explique comment interpréter le contenu, les activités de suivi, et leur corrélation, et comment analyser un grand nombre de suivis au cours de la résolution des problèmes.  
  
## Consultation du contenu de suivi  
 Un événement de suivi contient les informations significatives suivantes :  
  
-   Nom d'activité lorsqu'il est défini.  
  
-   Heure d'émission.  
  
-   Niveau de suivi.  
  
-   Nom de source de suivi.  
  
-   Nom du processus.  
  
-   ID de thread.  
  
-   Identificateur de suivi unique, qui est une URL qui pointe vers une destination dans MSDN Library en ligne, d'où vous pouvez obtenir plus d'informations concernant le suivi.  
  
 Toutes ces informations sont consultables dans le volet supérieur droit dans Service Trace Viewer, ou dans la section **Informations de base** dans la vue mise en forme du panneau inférieur droit lors de la sélection d'un suivi.  
  
> [!NOTE]
>  Si le client et le service se trouvent sur le même ordinateur, les suivis des deux applications seront présents.  Ils peuvent être filtrés à l'aide de la colonne **Nom du processus**.  
  
 De plus, la vue mise en forme fournit également une description du suivi et des informations détaillées supplémentaires lorsqu'elles sont disponibles.  Ces informations peuvent contenir le type d'exception et le message, les piles d'appel, l'action du message, les champs De\/À, et d'autres informations sur les exceptions.  
  
 Dans la vue XML, les balises xml utiles incluent les éléments suivants :  
  
-   \<SubType\> \(niveau de suivi\).  
  
-   \<TimeCreated\>.  
  
-   \<Source\> \(nom de source de suivi\).  
  
-   \<Correlation\> \(identificateur d'activité défini lors de l'émission du suivi\).  
  
-   \<Execution\> \(ID de processus et de thread\).  
  
-   \<Computer\>.  
  
-   \<ExtendedData\>, y compris \<Action\>, \<MessageID\> et \<ActivityId\> définis dans l'en\-tête du message lors de l'envoi d'un message.  
  
 Si vous examinez le suivi "Envoi d'un message sur un canal", vous pouvez consulter le contenu suivant.  
  
```  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
   <System xmlns="http://schemas.microsoft.com/2004/06/windows/eventlog/system">  
      <EventID>262163</EventID>  
      <Type>3</Type>  
      <SubType Name="Information">0</SubType>  
      <Level>8</Level>  
      <TimeCreated SystemTime="2006-08-04T18:45:30.8491051Z" />  
      <Source Name="System.ServiceModel" />  
       <Correlation ActivityID="{27c6331d-8998-43aa-a382-03239013a6bd}"/>  
       <Execution ProcessName="client" ProcessID="1808" ThreadID="1" />  
       <Channel />  
       <Computer>TEST1</Computer>  
   </System>  
   <ApplicationData>  
       <TraceData>  
          <DataItem>  
             <TraceRecord xmlns="http://schemas.microsoft.com/2004/10/E2ETraceEvent/TraceRecord" Severity="Information">  
                 <TraceIdentifier>http://msdn.microsoft.com/library/System.ServiceModel.Channels.MessageSent.aspx</TraceIdentifier>  
                 <Description>Sent a message over a channel.</Description>  
                 <AppDomain>client.exe</AppDomain>  
                 <Source>System.ServiceModel.Channels.ClientFramingDuplexSessionChannel/35191196</Source>  
                <ExtendedData xmlns="http://schemas.microsoft.com/2006/08/ServiceModel/MessageTransmitTraceRecord">  
  
                  <MessageProperties>  
                     <AllowOutputBatching>False</AllowOutputBatching>  
                  </MessageProperties>  
                  <MessageHeaders>  
                     <Action d4p1:mustUnderstand="1" xmlns:d4p1="http://www.w3.org/2003/05/soap-envelope" xmlns="http://www.w3.org/2005/08/addressing">http://Microsoft.ServiceModel.Samples/ICalculator/Multiply</Action>  
                     <MessageID xmlns="http://www.w3.org/2005/08/addressing">urn:uuid:7c6670d8-4c9c-496e-b6a0-2ceb6db35338</MessageID>  
                     <ActivityId CorrelationId="b02e2189-0816-4387-980c-dd8e306440f5" xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">27c6331d-8998-43aa-a382-03239013a6bd</ActivityId>  
                     <ReplyTo xmlns="http://www.w3.org/2005/08/addressing">  
                        <Address>http://www.w3.org/2005/08/addressing/anonymous</Address>  
                    </ReplyTo>  
                    <To d4p1:mustUnderstand="1" xmlns:d4p1="http://www.w3.org/2003/05/soap-envelope" xmlns="http://www.w3.org/2005/08/addressing">net.tcp://localhost/servicemodelsamples/service</To>  
                  </MessageHeaders>  
                  <RemoteAddress>net.tcp://localhost/servicemodelsamples/service</RemoteAddress>  
                </ExtendedData>  
            </TraceRecord>  
          </DataItem>  
       </TraceData>  
   </ApplicationData>  
</E2ETraceEvent>  
```  
  
## Suivi de ServiceModel E2E  
 Lorsque la source de suivi `System.ServiceModel` est définie avec un `switchValue` différent de « Désactivé » et `ActivityTracing`, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] crée des activités et des transferts pour le traitement [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].  
  
 Une activité est une unité logique de traitement qui regroupe tous les suivis liés à cette unité de traitement.  Par exemple, vous pouvez définir une activité pour chaque demande.  Les transferts créent une relation causale entre des activités dans des points de terminaison.  Propager l'ID d'activité vous permet de lier des activités sur des points de terminaison.  Cela peut être accompli en définissant `propagateActivity`\=`true` dans la configuration à chaque point de terminaison.  Les activités, les transferts et la propagation vous permettent d'effectuer la corrélation d'erreur.  De cette manière, vous pouvez rechercher plus rapidement l'origine d'une erreur.  
  
 Sur le client, une activité [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] est créée pour chaque appel de modèle objet \(par exemple, Ouvrir ChannelFactory, Ajouter, Diviser, et ainsi de suite.\) Chacun des appels d'opération est traité dans une activité « Traiter l'action ».  
  
 Dans la capture d'écran suivante, extraite de l'exemple [Tracing and Message Logging](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md), le volet gauche affiche la liste des activités créées dans le processus client, triées selon l'heure de création.  Vous trouverez ci\-dessous une liste chronologique des activités :  
  
-   Construction de la fabrication de canal \(ClientBase\).  
  
-   Ouverture de la fabrication de canal.  
  
-   Traitement de l'action Add.  
  
-   Configuration de la session sécurisée \(s'est produite à la première demande\) et traitement de trois messages de réponse d'infrastructure de sécurité : RST, RSTR, SCT \(traiter le message 1, 2, 3\).  
  
-   Traitement des demandes de soustraction, multiplication et division.  
  
-   Fermeture de la fabrication de canal, et ce faisant de la session sécurisée et traitement de la réponse de message de sécurité Cancel.  
  
 Les messages d'infrastructure de sécurité s'affichent à cause de l'élément wsHttpBinding.  
  
> [!NOTE]
>  Dans [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], nous affichons des messages de réponse qui sont traités initialement dans une activité séparée \(Traiter le message\) avant de les corréler à l'activité Traiter l'action correspondante qui inclut le message de demande, par le biais d'un transfert.  Cette opération a lieu pour les messages d'infrastructure et les demandes asynchrones et tient au fait que nous devons inspecter le message, lire l'en\-tête activityId et identifier l'activité Traiter l'action existante avec cet ID pour le corréler.  Pour les demandes synchrones, nous attendons la réponse et donc nous savons à quelle activité de traitement d'action se rapporte la réponse.  
  
 ![Utilisation de la visionneuse de trace](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace4.gif "e2eTrace4")  
Activités clientes WCF répertoriées selon l'heure de création \(volet gauche\) et leurs activités et suivis imbriqués \(volet supérieur droit\)  
  
 Lorsque nous sélectionnons une activité dans le volet gauche, le volet supérieur droit affiche des activités et des suivis imbriqués.  Par conséquent, il s'agit d'une vue hiérarchique réduite de la liste des activités de gauche basées sur l'activité parente sélectionnée.  Comme l'activité « Traiter l'action Add » sélectionnée est la première demande effectuée, cette activité contient l'activité Configurer une session sécurisée \(transférer vers, transférer en retour\) et les suivis du traitement réel de l'action Ajouter.  
  
 En double\-cliquant sur l'activité « Traiter l'action Add » dans le volet gauche, une représentation graphique des activités [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] clientes liées à l'activité Ajouter est affichée.  La première activité à gauche est l'activité racine \(0000\), l'activité par défaut.  [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] transfère l'activité ambiante.  Si celle\-ci n'est pas définie, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] transfère hors de 0000.  Dans ce contexte, la deuxième activité \(« Traiter l'action Add »\) transfère hors de 0.  Elle est suivie de Configurer la session sécurisée.  
  
 ![Utilisation de la visionneuse de trace](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace5.gif "e2eTrace5")  
Vue graphique des activités clientes de WCF : activité ambiante \(ici 0\), Traiter l'action et Configurer une session sécurisée  
  
 Dans le volet supérieur droit, nous pouvons consulter tous les suivis se rapportant à l'activité Traiter l'action Add.  Spécifiquement, nous avons envoyé le message de demande \(« Envoi d'un message sur un canal »\) et avons reçu la réponse \(« Réception d'un message sur un canal »\) dans la même activité.  Ce cas est illustré dans le graphique suivant.  À des fins de clarté, l'activité Configurer une session sécurisée est réduite dans le graphique.  
  
 ![Utilisation de la visionneuse de trace](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace6.gif "e2eTrace6")  
Liste de suivis pour l'activité Traiter l'action : nous envoyons la demande et recevons la réponse dans la même activité.  
  
 Dans ce contexte, nous chargeons uniquement des suivis clients à des fins de clarté, mais les suivis de service \(message de demande reçu et message de réponse envoyé\) apparaissent dans la même activité s'ils sont également chargés dans l'outil et que `propagateActivity` a pris la valeur `true.` . Cela est illustré plus loin.  
  
 Sur le service, le modèle d'activité est mappé aux concepts [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] comme suit :  
  
1.  Nous construisons et ouvrons un ServiceHost \(cela peut créer plusieurs activités associées à l'hôte, par exemple, dans le cas de la sécurité\).  
  
2.  Nous créons une activité Écouter à pour chaque écouteur dans le ServiceHost \(avec des transferts en entrée et en sortie de l'activité Ouvrir ServiceHost\).  
  
3.  Lorsque l'écouteur détecte une demande de communication initialisée par le client, il transfère à une activité « Recevoir des octets », dans laquelle tous les octets envoyés à partir du client sont traités.  Dans cette activité, nous pouvons voir les erreurs de connexion qui se sont produites pendant l'interaction du service et du client.  
  
4.  Pour chaque jeu d'octets reçu qui correspond à un message, nous traitons ces octets dans une activité « Traiter le message » où nous créons l'objet Message [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].  Dans cette activité, nous constatons des erreurs dues à un message erroné ou à une enveloppe incorrecte.  
  
5.  Une fois que le message est formé, nous transférons à une activité Traiter l'action.  Si `propagateActivity` a la valeur `true` sur le client et le service, cette activité a le même identificateur que celui défini dans le client et décrit précédemment.  À partir de cette étape, nous commençons à bénéficier de la corrélation directe sur des points de terminaison, car tous les suivis émis dans [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] liés à la demande appartiennent à cette même activité, y compris le traitement du message de réponse.  
  
6.  Pour les actions out\-of\-process, nous créons une activité « Exécuter le code utilisateur » pour isoler les suivis émis dans le code utilisateur de ceux émis dans [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].  Dans l'exemple précédent, le suivi « Le service envoie la réponse Ajouter » est émis dans l'activité « Exécuter le code utilisateur », pas dans l'activité propagée par le client, le cas échéant.  
  
 Dans l'illustration suivante, la première activité à gauche est l'activité racine \(0000\), l'activité par défaut.  Les trois activités suivantes consistent à ouvrir le ServiceHost.  L'activité dans la colonne 5 est l'écouteur, et les activités restantes \(6 à 8\) décrivent le traitement WCF d'un message, du traitement des octets à l'activation du code utilisateur.  
  
 ![Utilisation de la visionneuse de trace](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace7.gif "e2eTrace7")  
Liste des activités de service WCF  
  
 La capture d'écran suivante affiche les activités pour le client et le service, et met en surbrillance l'activité Traiter l'action Add dans les processus \(orange\).  Les flèches lient les messages de demande et de réponse envoyés et reçus par le client et le service.  Les suivis de Traiter l'action sont séparés par processus dans le graphique, mais sont affichés dans le cadre de la même activité dans le volet supérieur droit.  Dans ce volet, nous pouvons voir les suivis clients pour les messages envoyés qui précèdent les suivis de service pour les messages reçus et traités.  
  
 ![Utilisation de la visionneuse de trace](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace8.gif "e2eTrace8")  
Vue graphique des activités de client et de service WCF  
  
 Dans le scénario d'erreur suivant, les suivis d'erreur et d'avertissement au niveau du service et du client sont liés.  Une exception est levée d'abord dans le code utilisateur sur le service \(activité verte la plus à droite qui inclut un suivi d'avertissement pour l'exception « Le service ne peut pas traiter cette demande dans le code utilisateur »\).  Lorsque la réponse est envoyée au client, un suivi d'avertissement est encore émis pour désigner le message d'erreur \(activité rose à gauche\).  Le client ferme ensuite son client WCF \(activité jaune sur le côté inférieur gauche\) qui abandonne la connexion au service.  Le service génère une erreur \(activité rose la plus longue, à droite\).  
  
 ![Utilisation de la visionneuse de trace](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc\_e2etrace9s")  
Corrélation d'erreurs dans le service et le client  
  
 L'exemple utilisé pour générer ces suivis est une série de demandes synchrones qui utilisent wsHttpBinding.  Les scénarios sans sécurité présentent des différences par rapport à ce graphique, ou dans le cas des demandes asynchrones, dans lesquelles l'activité Traiter l'action comprend les opérations de début et de fin qui constituent l'appel asynchrone, et affiche les transferts vers une activité de rappel.  Pour plus d'informations sur des scénarios supplémentaires, consultez [Scénarios de suivi de bout en bout](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
## Résolution des problèmes à l'aide de Service Trace Viewer  
 Lorsque vous chargez des fichiers de suivi dans l'outil Service Trace Viewer, vous pouvez sélectionner une activité rouge ou jaune dans le volet gauche pour localiser la cause d'un problème dans votre application.  En général, l'activité 000 contient des exceptions non prises en charge qui se présentent à l'utilisateur.  
  
 ![Utilisation de la visionneuse de trace](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace10.gif "e2eTrace10")  
Sélection de l'activité rouge ou jaune pour localiser l'origine d'un problème  
  
 Dans le volet supérieur droit, vous pouvez examiner des suivis de l'activité que vous avez sélectionnée sur la gauche.  Vous pouvez examiner ensuite des suivis rouges ou jaunes dans ce volet et observer la manière dont ils sont corrélés.  Dans le graphique précédent, nous voyons des suivis d'avertissement à la fois pour le client et le service dans la même activité Traiter l'action.  
  
 Si ces suivis n'indiquent pas l'origine de l'erreur, vous pouvez utiliser le graphique en double\-cliquant sur l'activité sélectionnée dans le volet gauche \(ici, Traiter l'action\).  Puis le graphique avec les activités connexes est affiché.  Vous pouvez développer ensuite des activités connexes \(en cliquant sur les signes « \+ »\) pour rechercher le premier suivi émis en rouge ou en jaune dans une activité connexe.  Continuez à développer les activités qui se sont produites avant le suivi rouge ou jaune présentant un intérêt, les transferts aux flux d'activités ou de messages connexes sur des points de terminaison, jusqu'à ce que vous localisiez l'origine du problème.  
  
 ![Utilisation de la visionneuse de trace](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc\_e2etrace9s")  
Développement des activités pour localiser l'origine d'un problème  
  
 Si `ActivityTracing` ServiceModel est désactivé mais le suivi ServiceModel est activé, vous pouvez consulter des suivis ServiceModel émis dans l'activité 0000.  Toutefois, la corrélation de ces suivis demande un effort d'interprétation plus grand.  
  
 Si l'enregistrement des messages est activé, vous pouvez utiliser l'onglet Message pour voir quel message est concerné par l'erreur.  En double\-cliquant sur un message en rouge ou en jaune, vous pouvez consulter la vue graphique des activités connexes.  Ces activités sont celles qui sont le plus étroitement liées à la demande où une erreur s'est produite.  
  
 ![Utilisation de la visionneuse de trace](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace11.gif "e2eTrace11")  
Pour commencer la résolution des problèmes, vous pouvez aussi sélectionner un suivi de message rouge ou jaune et double\-cliquer dessus pour localiser l'origine.  
  
## Voir aussi  
 [Scénarios de suivi de bout en bout](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)   
 [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)   
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)