---
title: "Option d&#39;encodage d&#39;instance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Option d&#39;encodage d&#39;instance
La propriété **Option d'encodage d'instance** du magasin d'instances de workflow SQL vous permet de spécifier si le fournisseur de persistance SQL doit compresser les informations de l'état de l'instance du workflow à l'aide de l'algorithme Gzip avant d'enregistrer les informations dans la base de données de persistance.Les valeurs autorisées pour cette propriété sont : Gzip et Aucun.La valeur par défaut est None.La liste suivante décrit ces trois options.  
  
1.  **Gzip**.Le fournisseur de persistance encode les informations d'état à l'aide de l'algorithme Gzip avant de rendre les informations d'état persistantes dans la base de données de persistance.  
  
2.  **Aucun**Le fournisseur de persistance n'encode pas les informations d'état avant d'enregistrer les informations dans la base de données de persistance.  
  
 L'encodage des informations de l'état de l'instance du workflow à l'aide du Gzip réduit la consommation de mémoire dans la base de données SQL ainsi que la consommation réseau si la base de données réside sur un autre ordinateur sur le réseau différent de l'ordinateur sur lequel l'hôte du service de workflow s'exécute.Il est recommandé de définir la propriété **Option d'encodage d'instance** sur **Aucun** si l'état de l'instance de workflow est réduit.