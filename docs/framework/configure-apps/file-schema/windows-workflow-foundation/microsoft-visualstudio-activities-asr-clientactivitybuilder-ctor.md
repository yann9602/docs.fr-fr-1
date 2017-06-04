---
title: "Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: 
  - "Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor"
apilocation: 
  - "Microsoft.VisualStudio.Activities.dll"
apitype: "Assembly"
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
Crée une instance de la classe [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md).  
  
## Syntaxe  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
  
```  
  
#### Paramètres  
  
## Valeurs du paramètre  
 *operationDescription*  
  
 Décrit l'opération à effectuer dans l'activité de workflow qui doit être générée, notamment le nom de l'opération, le type de retour et les informations de paramètre.  La valeur de ce paramètre ne doit pas être **null**.  Elle doit décrire une opération synchrone qui utilise un contrat de message et prend un argument avec un message.  Si ces conditions ne sont pas satisfaites, le résultat d'exécution du constructeur et des autres méthodes de cette classe est indéfini.  
  
 *configurationName*  
  
 Spécifie le nom de configuration du point de terminaison.  La valeur de ce paramètre ne doit pas être **null** ou vide.  Si ces conditions ne sont pas satisfaites, le résultat d'exécution du constructeur et des autres méthodes de cette classe est indéfini.  
  
 *proxyNamespace*  
  
 Spécifie l'espace de noms du service pour l'opération.  La valeur de ce paramètre ne doit pas être **null** ou vide.  Si ces conditions ne sont pas satisfaites, le résultat d'exécution du constructeur et des autres méthodes de cette classe est indéfini.  
  
## Voir aussi  
 [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)