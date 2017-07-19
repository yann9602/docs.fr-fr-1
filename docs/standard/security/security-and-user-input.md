---
title: "S&#233;curit&#233; et entr&#233;es d&#39;utilisateur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sécurité du code, entrée d'utilisateur"
  - "codage sécurisé, entrée d'utilisateur"
  - "sécurité (.NET Framework), entrée d'utilisateur"
  - "entrée d'utilisateur, sécurité"
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# S&#233;curit&#233; et entr&#233;es d&#39;utilisateur
Les données utilisateur, qui correspondent à n'importe quelles entrées \(données provenant d'une demande Web ou URL, entrées dans les contrôles d'une application Microsoft Windows Forms etc.\), peuvent nuire au code car il arrive souvent que ces données soient utilisées directement comme paramètres pour appeler d'autre code.  Cette situation est semblable aux appels effectués dans votre code par du code nuisible avec des paramètres étranges, et les mêmes précautions doivent être observées.  Les entrées de l'utilisateur sont en fait plus difficiles à sécuriser car il n'existe pas de frame de pile pour détecter la présence de données potentiellement non fiables.  
  
 Ces données comptent parmi les bogues de sécurité les plus difficiles et les plus subtiles à détecter car même si elles peuvent exister dans du code apparemment sans rapport avec la sécurité, elles correspondent à une passerelle permettant de transmettre les données incorrectes à d'autre code.  Pour rechercher ces bogues, suivez n'importe quel type de données d'entrée, imaginez l'éventail des valeurs possibles, puis considérez si le code confronté à ces données peut traiter tous ces cas.  Vous pouvez corriger ces bogues en vérifiant les plages et en rejetant toutes les entrées que le code ne peut pas traiter.  
  
 Certaines considérations importantes relatives aux données utilisateur sont notamment les suivantes :  
  
-   Toutes les données utilisateur dans une réponse de serveur s'exécutent dans le contexte du site du serveur sur le client.  Si votre serveur Web prend des données utilisateur et les insère dans la page Web retournée, il peut, par exemple, inclure une balise **\<script\>** et s'exécuter comme depuis le serveur.  
  
-   N'oubliez pas que le client peut demander n'importe quelle URL.  
  
-   Considérez des chemins d'accès non valides ou délicats :  
  
    -   ..\\ , des chemins d'accès particulièrement longs ;  
  
    -   l'utilisation de caractères génériques \(\*\) ;  
  
    -   l'expansion de jeton \(%token%\) ;  
  
    -   des formes étranges de chemins d'accès dont la signification est particulière ;  
  
    -   l'alternance de noms de flux de systèmes de fichier comme par exemple `filename::$DATA` ;  
  
    -   des versions courtes de noms de fichiers comme par exemple `longfi~1` pour `longfilename` ;  
  
-   N'oubliez pas que Eval\(userdata\) peut faire n'importe quoi.  
  
-   Méfiez\-vous de la liaison tardive à un nom qui inclut des données utilisateur.  
  
-   Si vous traitez des données Web, considérez les différentes formes d'échappement qui sont autorisées, y compris :  
  
    -   échappements hexadécimaux \(%nn\) ;  
  
    -   échappements Unicode \(%nnn\) ;  
  
    -   échappements très long UTF\-8 \(%nn%nn\) ;  
  
    -   doubles échappements \(%nn devient %mmnn, où %mm correspond à l'échappement de '%'\) ;  
  
-   Méfiez\-vous des noms d'utilisateur qui peuvent avoir plus d'un format canonique ;  par exemple, dans Microsoft Windows 2000, vous pouvez souvent utiliser soit la forme MONDOMAINE\\*nom\_utilisateur*, soit la forme *nom\_utilisateur*@mondomaine.exemple.com.  
  
## Voir aussi  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)