---
title: "Composant logiciel enfichable MMC Configuration WS-AtomicTransaction | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# Composant logiciel enfichable MMC Configuration WS-AtomicTransaction
Le composant logiciel enfichable MMC Configuration WS\-AtomicTransaction est utilisé pour configurer une partie des paramètres WS\-AtomicTransaction sur les ordinateurs locaux et distants.  
  
## Notes  
 Si vous exécutez [!INCLUDE[wxp](../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], vous pouvez accéder au composant logiciel enfichable MMC ; pour cela, naviguez jusqu'à **Panneau de configuration\/Outils d'administration\/Services de composants**, puis cliquez avec le bouton droit sur **Poste de travail**, et sélectionnez **Propriétés**.C'est le même emplacement que celui dans lequel vous pouvez configurer le MSDTC.Les options disponibles pour la configuration sont groupées sous l'onglet **WS\-AT**.  
  
 Si vous exécutez Windows Vista ou [!INCLUDE[lserver](../../../includes/lserver-md.md)], le composant logiciel enfichable MMC est accessible en cliquant sur le bouton **Démarrer** et en tapant `dcomcnfg.exe` dans la zone **Rechercher**.Lorsque la console MMC est ouverte, naviguez jusqu'au nœud **Poste de travail\\Distributed Transaction Coordinator\\Local DTC**, cliquez avec le bouton droit et sélectionnez **Propriétés**.Les options disponibles pour la configuration sont groupées sous l'onglet **WS\-AT**.  
  
 Les étapes précédentes sont utilisées pour lancer le composant logiciel enfichable afin de configurer un ordinateur local.Si vous souhaitez configurer un ordinateur distant, vous devez rechercher son nom dans **Panneau de configuration\/Outils d'administration\/Services de composants\/**, et exécuter la même procédure si vous utilisez [!INCLUDE[wxp](../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../includes/ws2003-md.md)].Si vous utilisez Windows Vista ou [!INCLUDE[lserver](../../../includes/lserver-md.md)], suivez les étapes précédentes correspondantes pour Vista et [!INCLUDE[lserver](../../../includes/lserver-md.md)], mais utilisez le nœud **Distributed Transaction Coordinator\\Local DTC** sous le nœud de l'ordinateur distant.  
  
 Pour utiliser l'interface utilisateur fournie par l'outil, vous devez enregistrer le fichier WsatUI.dll, situé à l'emplacement suivant :  
  
 **%PROGRAMFILES%\\Microsoft SDKs\\Windows\\v6.0\\Bin\\WsatUI.dll**  
  
 L'inscription peut être faite par la commande suivante.  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 Vous pouvez utiliser cet outil pour modifier les paramètres de base WS\-AtomicTransaction.Par exemple, vous pouvez activer et désactiver le support de protocole de WS\-AtomicTransaction, configurer les ports HTTP pour WS\-AT, lier un certificat SSL au port HTTP, configurer des certificats en spécifiant les noms de sujet correspondants, sélectionner le mode de suivi et définir la valeur par défaut et les délais d'attente maximum.  
  
 Si vous devez configurer uniquement le support WS\-AtomicTransaction sur l'ordinateur local, vous pouvez utiliser la version de ligne de commande de cet outil.[!INCLUDE[crabout](../../../includes/crabout-md.md)] l'outil en ligne de commande, consultez la rubrique de [Utilitaire de configuration WS\-AtomicTransaction \(wsatConfig.exe\)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).  
  
 Sachez que le composant logiciel enfichable MMC et l'outil de ligne de commande ne prennent pas en charge la configuration de tous les paramètres WS\-AT.Ces paramètres ne peuvent être modifiés qu'en modifiant directement le registre.[!INCLUDE[crabout](../../../includes/crabout-md.md)] ces paramètres du Registre, consultez [Configuration de la prise en charge WS\-Atomic Transaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
### Description de l'interface utilisateur  
 **Activer le support réseau WS\-Atomic Transaction** :  
  
 Lorsque vous sélectionnez ou désélectionnez cette case à cocher, cela active ou désactive tous les composants d'interface utilisateur de ce composant logiciel enfichable.  
  
 Avant d'activer cette case à cocher, vous devez vous assurer que l'accès au réseau DTC est activé \(communications entrantes ou sortantes, ou encore les deux\).Cette valeur peut être vérifiée sous l'onglet **Sécurité** du composant logiciel enfichable MSDTC.  
  
#### Zone de groupe Réseau  
 Vous pouvez spécifier le port HTTPS et des paramètres de sécurité supplémentaires, tels que le chiffrement SSL dans le groupe Réseau.Ce groupe est désactivé \(grisé\) si les transactions réseau DTC ne sont pas activées.  
  
 **Port HTTPS**  
  
 C'est la valeur du port HTTPS utilisée pour WS\-AT.Cette valeur doit être un nombre compris dans la plage 1\-65535 \(pour représenter un port valide\).La modification du port HTTP modifie la configuration du service HTTP, ce qui signifie que l'adresse de service WS\-AT utilisée précédemment est libérée et qu'une nouvelle adresse de service WS\-AT est enregistrée sur la base du nouveau port.De plus, le port que vous venez de sélectionner est chiffré avec le certificat sélectionné pour le chiffrement SSL.  
  
> [!NOTE]
>  Si vous avez déjà activé le pare\-feu avant d'exécuter cet outil, le port est enregistré automatiquement dans la liste d'exceptions.Si le pare\-feu est désactivé avant l'exécution de cet outil, aucun élément supplémentaire n'est configuré concernant le pare\-feu.  
  
 Si vous activez le pare\-feu après avoir configuré WS\-AT, vous devez réexécuter cet outil et fournir le numéro de port à l'aide de ce paramètre.Si vous désactivez le pare\-feu après la configuration, WS\-AT continue à fonctionner sans entrée supplémentaire.  
  
 **Certificat de point de terminaison**  
  
 Si vous cliquez sur le bouton **Sélectionner**, cela affiche la liste des certificats actuellement disponibles sur l'ordinateur local ; l'utilisateur peut ainsi sélectionner le certificat pouvant être utilisé pour le chiffrement SSL.Les certificats doivent posséder une clé privée.Si ce n'est pas le cas, un message d'erreur s'affiche.  
  
> [!NOTE]
>  Lorsque vous définissez un certificat SSL pour un port sélectionné, vous remplacez le certificat SSL d'origine associé à ce port, le cas échéant.  
  
 **Comptes autorisés**  
  
 Si vous cliquez sur le bouton **Sélectionner**, l'éditeur de la liste de contrôle d'accès Windows est appelé ; vous pouvez y spécifier l'utilisateur ou le groupe autorisé à participer à WS\-AtomicTransaction en activant la zone **Autoriser** ou **Refuser** dans le groupe d'autorisations **Participer**.  
  
 **Certificats autorisés**  
  
 Si vous cliquez sur le bouton **Sélectionner**, la liste des certificats actuellement disponibles sur LocalMachine s'affiche.Vous pouvez sélectionner ensuite les identités de certificat autorisées à participer à WS\-AtomicTransaction.  
  
#### Zone de groupe Délai d'attente  
 La zone de groupe **Délai d'attente** permet de spécifier le délai d'attente par défaut maximal applicable à WS\-Atomic Transaction.Les valeurs valides de délai d'attente sortant sont comprises entre 1 et 3 600.Les valeurs valides de délai d'attente entrant sont comprises entre 0 et 3 600.  
  
#### Zone de groupe Suivi et journalisation  
 La zone de groupe **Suivi et journalisation** permet de configurer le niveau souhaité de suivi et de journalisation.  
  
 Si vous cliquez sur le bouton **Options**, une page est appelée, dans laquelle vous pouvez spécifier des paramètres supplémentaires.  
  
 La zone de liste déroulante **Niveau de suivi** permet de sélectionner une valeur parmi les valeurs valides de l'énumération <xref:System.Diagnostics.TraceLevel>.Vous pouvez également utiliser les cases à cocher pour spécifier si vous souhaitez exécuter le suivi des activités, la propagation d'activité ou le rassemblement d'informations d'identification personnelles \(PII\).  
  
 Vous pouvez également spécifier des sessions de journalisation dans la zone de groupe **Session de journalisation**.  
  
> [!NOTE]
>  Lorsqu'un autre consommateur de suivi utilise le fournisseur de suivi WS\-AT, vous ne pouvez pas créer de nouvelle session de journalisation pour les événements de suivi.Toute tentative de configuration de la journalisation pendant cette période aboutit à l'affichage du message d'erreur suivant : Impossible d'activer le fournisseur.Code d'erreur :1  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] le suivi et la journalisation, consultez [Administration et diagnostics](../../../docs/framework/wcf/diagnostics/index.md).  
  
## Voir aussi  
 [Configuration de la prise en charge WS\-Atomic Transaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)   
 [Utilitaire de configuration WS\-AtomicTransaction \(wsatConfig.exe\)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)   
 [Administration et diagnostics](../../../docs/framework/wcf/diagnostics/index.md)