---
title: "&lt;liaisons&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;liaisons&gt;
Cette section contient une collection de liaisons standard et personnalisées.  Chaque entrée est un élément de `binding` qui peut être identifié par son `name` unique.  Les services utilisent les liaisons en les liant à l'aide de `name`.  Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.  Pour plus d'informations sur la configuration par défaut, ainsi que sur les comportements et les liaisons sans nom, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## Liaison fournie par le système  
 Les liaisons fournies par le système masquent la complexité de la pile de la messagerie du WCF.  Les applications qui utilisent des liaisons fournies par le système ne requièrent pas de contrôle total sur la pile.  Les attributs exposés sur chaque liaison fournie par le système sont les plus appropriés pour le scénario d'utilisation des adresses de liaison.  
  
 La section de configuration de chaque liaison fournie par le système peut définir plusieurs configurations utilisées en vue de configurer la liaison.  Chaque configuration est identifiée par un nom unique.  
  
 Il n'est pas possible d'ajouter des éléments ou des attributs à une liaison fournie par le système.  Pour cela, vous devez implémenter une liaison personnalisée, telle que décrite dans la section « Liaison personnalisée » de cette rubrique.  Il est possible de définir une liaison personnalisée qui imite parfaitement une liaison fournie par le système et ajoute quelques paramètres sur lesquels l'utilisateur de l'application souhaite avoir le contrôle.  
  
 Pour obtenir une liste des liaisons fournies par le système, consultez [Liaisons fournies par le système](../../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## Liaison personnalisée  
 Les liaisons personnalisées permettent d'exercer un contrôle total sur la pile de messagerie WCF.  Une liaison individuelle définit la pile de messages en spécifiant les éléments de configuration des éléments de la pile suivant leur l'ordre d'apparition dans cette pile.  Chaque élément définit et configure l'élément de la pile.  Il doit y avoir un seul élément de `transport` dans chaque liaison personnalisée.  Sans cet élément, la pile de messagerie est incomplète.  
  
 L'ordre dans lequel les éléments apparaissent dans la pile est important car il s'agit de l'ordre dans lequel les opérations sont appliquées au message.  Voici l'ordre requis des éléments de la pile :  
  
1.  Transactions \(facultatif\)  
  
2.  Messagerie fiable \(facultatif\)  
  
3.  Sécurité \(facultatif\)  
  
4.  Encodeur  
  
5.  Transport  
  
 Les liaisons personnalisées sont identifiées par leur attribut `name`.  Pour plus d'informations sur les liaisons personnalisées, consultez [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.BindingsSection>   
 <xref:System.ServiceModel.Channels.Binding>   
 <xref:System.ServiceModel.Channels.BindingElement>   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)