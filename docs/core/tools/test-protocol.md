---
title: Protocole de communication de test des outils CLI .NET Core
description: Protocole de communication de test des outils CLI .NET Core
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 88cba792-3640-41de-b55d-00f575e9d5e2
translationtype: Human Translation
ms.sourcegitcommit: 81e7604f0a646e5de9c2ed35ff3b6ef6d7fb2e71
ms.openlocfilehash: a35385cbb08614493fdcfc74504b00178dc532ea

---

#<a name="net-core-cli-test-communication-protocol"></a>Protocole de communication de test des outils CLI .NET Core

## <a name="introduction"></a>Introduction
Chaque fois que vous passez un port à dotnet-test, la commande est exécutée au moment du design. Cela signifie que dotnet-test se connecte à ce port à l’aide du protocole TCP et qu’il échange ensuite un ensemble établi de messages avec les autres éléments connectés à ce port. Quand cela se produit, le Test Runner reçoit également un nouveau port qui est utilisé par dotnet-test pour communiquer avec lui. Le Test Runner utilise également le protocole TCP pour communiquer avec dotnet-test, car en mode Design, il ne suffit pas d’afficher les résultats dans la console. La commande doit envoyer les messages concernant la structure de l’adaptateur qui contiennent les résultats de l’exécution du test.

### <a name="communication-protocol-at-design-time"></a>Protocole de communication au moment du design

1. Étant donné qu’au moment du design, dotnet-test se connecte à un port lorsqu’il démarre, l’adaptateur doit écouter ce port, sous peine d’échouer. De cette façon, l’adaptateur peut réserver tous les ports dont il a besoin en établissant une liaison avec ces ports et en les écoutant avant que dotnet-test ne soit exécuté et tente d’obtenir des ports pour le Test Runner.
2. Une fois que dotnet-test est démarré, il envoie un message TestSession.Connected à l’adaptateur indiquant qu’il est prêt à recevoir des messages.
3. Il est possible d’envoyer un message facultatif de [vérification de la version](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Messages/ProtocolVersionMessage.cs) contenant la version de l’adaptateur du protocole. Dotnet-test renvoie ensuite la version du protocole qu’il prend en charge.

Tous les messages ont le format décrit ici : [Message.cs](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Messages/Message.cs). Pour connaître le format de charge utile de chaque message, cliquez sur les liens associés aux classes utilisées pour sérialiser/désérialiser les informations contenues dans la description du protocole.

#### <a name="test-execution"></a>Exécution de tests
![Exécution de tests](./media/test-protocol/dotnet-test-execute.png)

1. Après la vérification de version facultative, l’adaptateur envoie un TestExecution.GetTestRunnerProcessStartInfo, contenant les [tests](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Messages/RunTestsMessage.cs) qu’il souhaite exécuter. Dotnet-test renvoie un FileName et un Arguments dans une charge utile [TestStartInfo](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.DotNet.Tools.Test/TestStartInfo.cs), que l’adaptateur peut utiliser pour démarrer le Test Runner. Auparavant, la liste des tests à exécuter était envoyée dans le cadre de l’argument. Toutefois, pour certains projets de test, cela provoquait le dépassement de la taille limite autorisée par la ligne de commande.
  1. Dans le cadre de ces arguments, nous envoyons un port auquel le Test Runner doit se connecter, et, pour l’exécution des tests, un indicateur --wait-command, qui indique que le Test Runner doit se connecter au port et attendre les commandes, au lieu de poursuivre l’exécution des tests.
2. À ce stade, l’adaptateur peut lancer le Test Runner (et s’attacher à celui-ci pour le débogage, le cas échéant).
3. Une fois le Test Runner démarré, il envoie à dotnet-test un message TestRunner.WaitCommand indiquant qu’il est prêt à recevoir des commandes. Dotnet-test envoie alors un TestRunner.Execute avec la liste des [tests](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Messages/RunTestsMessage.cs) à exécuter. Cela permet de contourner la limite de taille de ligne de commande décrite ci-dessus.
4. Le Test Runner envoie ensuite à dotnet-test (qui le transfère à l’adaptateur) un TestExecution.TestStarted contenant les informations de [test](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Test.cs) au début de chaque test.
5. Le Test Runner envoie également à dotnet-test (qui le transfère à l’adaptateur) un TestExecution.TestResult contenant les [résultats](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/TestResult.cs) de chaque test.
6. Une fois tous les tests terminés, le Test Runner envoie un message TestRunner.Completed à dotnet-test, que celui-ci envoie en tant que TestExecution.Completed à l’adaptateur.
7. Quand l’adaptateur a terminé, il envoie à dotnet-test un TestSession.Terminate, ce qui entraîne l’arrêt de dotnet-test.

#### <a name="test-discovery"></a>Découverte des tests
![Découverte des tests](./media/test-protocol/dotnet-test-discover.png)

1. Après la vérification de version facultative, l’adaptateur envoie un message TestDiscovery.Start. Dans ce cas, l’adaptateur n’a pas besoin d’être attaché au processus. Dotnet-test démarre donc le Test Runner lui-même. De plus, puisque vous n’avez pas à passer une longue liste d’arguments au Test Runner, il est inutile de lui passer l’indicateur --wait-command. Dotnet-test passe uniquement un argument --list au Test Runner, ce qui signifie que ce dernier ne doit pas exécuter les tests, mais simplement les lister.
2. Le Test Runner envoie ensuite à dotnet-test (qui le transfère ensuite à l’adaptateur) un TestDiscovery.TestFound pour chaque [test](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Test.cs) trouvé.
3. Une fois tous les tests découverts, le Test Runner envoie un message TestRunner.Completed à dotnet-test, que celui-ci envoie en tant que TestDiscovery.Completed à l’adaptateur.
4. Quand l’adaptateur a terminé, il envoie à dotnet-test un TestSession.Terminate, ce qui entraîne l’arrêt de dotnet-test.


<!--HONumber=Nov16_HO1-->


