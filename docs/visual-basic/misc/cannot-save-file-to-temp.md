---
title: "Impossible d’enregistrer le fichier dans TEMP | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID735"
ms.assetid: 1055fc15-9641-43b2-a40c-a0a9fbbb34b2
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Impossible d’enregistrer le fichier dans TEMP
Soit un composant ne trouve pas de répertoire nommé TEMP, soit le lecteur ou la partition contenant le répertoire TEMP ne dispose pas de suffisamment d’espace pour enregistrer les informations.  
  
### Pour corriger cette erreur  
  
1.  Créez un répertoire nommé « TEMP » et affectez son chemin comme valeur de la variable d’environnement TEMP.  
  
2.  Libérez de l’espace sur le disque en supprimant des fichiers inutiles ou créez un répertoire TEMP sur une autre partition et affectez son chemin comme valeur de la variable d’environnement TEMP.  
  
## Voir aussi  
 [Error Types](../../visual-basic/programming-guide/language-features/error-types.md)