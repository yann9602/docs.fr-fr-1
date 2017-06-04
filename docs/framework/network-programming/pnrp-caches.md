---
title: "Caches PNRP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 270068d9-1b6b-4eb9-9e14-e02326bb88df
caps.latest.revision: 4
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 4
---
# Caches PNRP
Les caches équivalents de \(PNRP\) de fournisseur de résolution de noms sont des collections locales de points de terminaison homologues algorithmiquement sélectionnés mis à jour sur l'homologue.  
  
## Initialisation du cache de PNRP  
 Pour initialiser le cache de PNRP, ou la collection d'enregistrement de nom homologue, lorsqu'un nœud homologue démarre, un nœud peut utiliser les méthodes suivantes :  
  
-   Les entrées de cache persistantes qui était présent lorsque le nœud a été arrêté sont chargées de la mémoire de disque dur.  
  
-   Si une application utilise l'infrastructure de collaboration P2P, les informations de collaboration sont disponibles dans le gestionnaire de contacts pour ce nœud.  
  
## Mise à l'échelle la résolution de noms homologue avec un cache multiniveau  
 Pour que les tailles en cache de PNRP les petits, équivalents nœuds utilisent un cache multiniveau, dans lequel chaque niveau contient un nombre maximal d'entrée.  Chaque niveau dans le cache représente une partie un dixième plus petit de l'espace de numéro d'ID de PNRP \(2<sup>256</sup>\).  Le plus bas dans le cache contient un ID de PNRP localement stocké et d'autres ID de PNRP qui sont numériquement près de lui.  Comme un niveau du cache est rempli avec un maximum de 20 entrées, un nouveau niveau inférieur est créé.  Le nombre maximal de niveaux dans le cache est sur l'ordre du10journal \(nombre total d'ID de PNRP en nuage\).  Par exemple, pour un nuage global avec 100 millions d'ID de PNRP, il y a plus de 8 \(\=log10\(100.000.000\)\) niveaux dans le cache et un numéro de tronçons similaire pour résoudre un ID de PNRP pendant la résolution de noms.  Ce mécanisme permet d'une table de hachage distribuée pour laquelle un ID de PNRP arbitraire peut être résolu en effectuant le suivi des messages de demande de PNRP à l'homologue prochain\- proche jusqu'à ce que l'homologue à CPA correspondant soit trouvé.  
  
 Pour garantir que la résolution peut s'exécuter, chaque fois qu'un nœud ajoute une entrée au niveau le plus bas de son cache, il inonde une copie de l'entrée à tous les nœuds dans le dernier niveau du cache.  
  
 Les entrées de cache sont actualisées dans le temps.  Les entrées de cache qui sont périmées sont supprimées du cache.  Le résultat est que la table de hachage distribuée des ID de PNRP est basée sur les points de terminaison actifs, contrairement à DNS dans lequel les répondent à des enregistrements et le protocole DNS ne fournit aucune garantie que le nœud connexe avec l'adresse est active sur le réseau.  
  
## D'autres cache de PNRP  
 Un autre magasin de données persistant est le cache local.  En plus de les autres objets nécessaires pour l'activité de PNRP, il peut inclure des enregistrements associés à une session nuage ou de collaboration de PNRP qui est sécurisé publiée et synchronisée entre tous les membres du nuage.  Cette mémoire reproduite représente la vue des données du groupe, qui doivent être identiques pour tous les membres du groupe.  Techniquement, ces objets ne sont pas des enregistrements en tant que tel, mais plutôt la demande, la présence, et les données d'objets destinés au cache local.  L'utilisation du nuage de PNRP garantit que les objets sont propagées à tous les nœuds de la session de collaboration ou le nuage de PNRP.  La réplication d'enregistrement entre les membres nuage utilise le protocole SSL pour fournir le chiffrement et l'intégrité des données.  
  
 Lorsqu'un homologue joint un nuage, ils ne reçoivent pas automatiquement les données locales de cache de hébergent l'homologue auquel ils s'attachent ; ils doivent s'abonner à l'homologue hôte des mises à jour de l'application, la présence, et les données d'objet.  Après la synchronisation initiale, les homologues resynchronisent périodiquement leurs mémoires répliquées pour garantir que tous les membres du groupe ont régulièrement le même point de vue.  La session ou les applications de collaboration dans la session de collaboration peut également remplir la même fonction.  
  
 Une fois la session de collaboration démarrage d'un nuage, les applications peuvent stocker des homologues et démarrer de publication leurs informations à l'aide de la sécurité définie par la portée nuage.  Lorsqu'un homologue joint un nuage, les mécanismes de sécurité pour le nuage sont appliqués à l'homologue, en lui donnant une portée dans laquelle pour participer.  Les enregistrements peuvent ensuite être publiés sécurisé dans la portée du nuage.  Notez que la portée nuage peut ne pas être identique à l'étendue d'application de collaboration.  
  
 Les homologues peuvent stocker l'intérêt en recevant des objets d'autres équivalents.  Lorsqu'un objet est mis à jour, est averti l'application de collaboration et le nouvel objet est passé à tous les abonnés de l'application.  Par exemple, un homologue dans une application de groupe de conversation peut stocker l'intérêt en recevant des informations d'application, l'qui enverront tous les enregistrements de conversation comme données d'application.  Cela permet à la l'activité de conversation du moniteur dans le nuage.  
  
## Voir aussi  
 <xref:System.Net.PeerToPeer>