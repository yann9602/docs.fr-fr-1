---
title: "Outil XML Serializer Generator (Sgen.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Outil XML Serializer Generator (Sgen.exe)
L'outil XML Serializer Generator crée un assembly de sérialisation XML pour les types dans un assembly spécifié afin d'améliorer les performances de démarrage d'un <xref:System.Xml.Serialization.XmlSerializer> lorsqu'il sérialise ou désérialise les objets des types spécifiés.  
  
## Syntaxe  
  
```  
  
sgen [options]  
```  
  
#### Paramètres  
  
|Option|Description|  
|------------|-----------------|  
|**\/a**\[**ssembly**\]**:***nom de fichier*|Génère le code de sérialisation pour tous les types contenus dans l'assembly ou le fichier exécutable spécifié par *nom de fichier*.  Un seul nom de fichier peut être fourni.  Si cet argument est répété, le dernier nom de fichier est utilisé.|  
|**\/c\[ompiler\]:** *options*|Spécifie les options à passer au compilateur C\#.  Toutes les options csc.exe sont prises en charge à mesure qu'elles sont passées au compilateur.  Cette option peut être utilisée pour spécifier que l'assembly doit être signé et pour indiquer le fichier de clé.|  
|**\/d**\[**ebug**\]|Génère une image qui peut être utilisée avec un débogueur.|  
|**\/f\[orce\]**|Force l'écrasement par réécriture d'un assembly existant du même nom.  La valeur par défaut est **false**.|  
|**\/help or \/?**|Affiche la syntaxe et les options de commande de l'outil.|  
|**\/k**\[**eep**\]|Efface la suppression des fichiers source générés et d'autres fichiers temporaires une fois qu'ils ont été compilés dans l'assembly de sérialisation.  Cette option peut être utilisée afin de déterminer si l'outil génère le code de sérialisation pour un type particulier.|  
|**\/n**\[**ologo**\]|Supprime l'affichage de la bannière de démarrage Microsoft.|  
|**\/o**\[**ut**\]**:***chemin*|Spécifie le répertoire dans lequel enregistrer l'assembly généré. **Note:**  Le nom de l'assembly généré est composé du nom de l'assembly d'entrée suivi de"xmlSerializers.dll".|  
|**\/p**\[**roxytypes**\]|Génère un code de sérialisation uniquement pour les types de proxy de service Web XML.|  
|**\/r**\[**eference**\]**:***fichiers d'assemblys*|Spécifie les assemblys référencés par les types qui requièrent la sérialisation XML.  Accepte plusieurs fichiers d'assembly séparés par des virgules.|  
|**\/s**\[**ilent**\]|Supprime l'affichage des messages indiquant la réussite des opérations.|  
|**\/t**\[**ype**\]**:***type*|Génère un code de sérialisation uniquement pour le type spécifié.|  
|**\/v**\[**erbose**\]|Affiche la sortie en clair pour le débogage.  Répertorie les types à partir de l'assembly cible qui ne peuvent pas être sérialisés avec le <xref:System.Xml.Serialization.XmlSerializer>.|  
|**\/?**|Affiche la syntaxe et les options de commande de l'outil.|  
  
## Notes  
 Lorsque l'outil XML Serializer Generator n'est pas utilisé, un <xref:System.Xml.Serialization.XmlSerializer> génère un code de sérialisation et un assembly de sérialisation pour chacun des types chaque fois qu'une application est exécutée.  Pour améliorer les performances du démarrage de la sérialisation XML, utilisez l'outil Sgen.exe afin de générer ces assemblys à l'avance.  Ces assemblys peuvent ensuite être déployés avec l'application.  
  
 L'outil XML Serializer Generator peut également améliorer les performances des clients qui utilisent des proxies de service Web XML pour communiquer avec les serveurs car le processus de sérialisation n'entraîne pas de dégradation des performances lors du premier chargement du type.  
  
 Ces assemblys générés ne peuvent pas être utilisés du côté serveur d'un service Web.  Cet outil est conçu uniquement pour les clients de service Web et les scénarios de sérialisation manuelle.  
  
 Si l'assembly qui contient le type à sérialiser est nommé MyType.dll, l'assembly de sérialisation associé sera alors nommé MyType.XmlSerializers.dll.  
  
## Exemples  
 La commande suivante crée un assembly nommé Data.XmlSerializers.dll pour sérialiser tous les types contenus dans l'assembly nommé Data.dll.  
  
```  
sgen Data.dll   
```  
  
 L'assembly Data.XmlSerializers.dll peut être référencé à partir du code qui doit sérialiser et désérialiser les types dans Data.dll.  
  
## Voir aussi  
 [Tools](../../../docs/framework/tools/index.md)   
 [XML Web Services Overview](http://msdn.microsoft.com/fr-fr/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)   
 [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md)