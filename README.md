# Blockchain-ETH-

## DLT: Distributed ledger technology AKA Blockchain

Un registre distribué (aussi appelé registre partagé en anglais, distributed ledger ou shared ledger) est un registre simultanément enregistré et synchronisé sur un réseau d'ordinateurs, qui évolue par l'addition de nouvelles informations préalablement validées par l'entièreté du réseau et destinées à ne jamais être modifiées ou supprimées.

La téchnologie blockchain ont résolu 2 problèmes:

- l'immuabilité des données, elles ne peuvent pas être modifiées, elles sont inviolables.
- un processus distribué, les point d'autorité unique ou point de défaillance unique (SPOF => single point of authority). Chaque noeud travaille ensemble sur la base d'un mécanisme de consensus empêchant les acteurs malveillants.

## Immuabilité:

Dans une blockchain, toutes les transactions sont stockées dans un bloc. Chaqu'un de ces blocs inclus un system de "cryptographic hash", chaque bloc comprend le hachage du bloc précédent dans la blockchain, reliant les deux blocs, ainsi qu'un hash de toutes les transactions stockées dans le bloc.
La fonction de hash cryptographique est une fonction à sens unique (fonction non inversible) qui mappe le contenu d'un bloc sur un nombre.

![Image of Yaktocat](https://raw.githubusercontent.com/AbsoluteVirtueXI/alyra-courses/master/res/blockchain.jpeg)

### Ci-dessous comment ce type de processus peut-être implémenté avec du code:

![Image of Yaktocat](https://raw.githubusercontent.com/AbsoluteVirtueXI/alyra-courses/master/res/codeview.jpg)

### Ci-dessous un aperçu de base d'une en-tête de bloc:

![Image of Yaktocat](https://raw.githubusercontent.com/AbsoluteVirtueXI/alyra-courses/master/res/blockheader.png)

Ce processus confirme l'intégrité du bloc et tout le chemin jusqu'au bloc de origine (Genesis Block)
Si un acteur malveillant souhaite modifier un bloc, par exemple en modifiant le montant d'une transaction, il modifiera le hachage de toutes les transactions du bloc. Il devra donc miner à nouveau ce bloc.
Le processus modifiera le hachage du bloc entier, et tous les blocs suivants auront un hachage différent stocké dans leur header pour le bloc précédent. L'acteur malveillant devra donc extraire également tous les blocs suivants en fonction du hachage du bloc malveillant conçu.
L'autre protection qui empêche ce type de modifications est un mécanisme de consensus. Les attaquants devraient contrôler 51% du réseau pour inverser les qui ont déjà eu lieu dans une blockchain. Ceci est connu sous le nom d'attaque des 51%. Inutile de dire que cela est en fait impossible, les attaquants auraient besoin de beaucoup de puissanc de calcul, et même s'ils réussissent, cela invaliderait la confiance dans cette blockchain et les utilisateurs partiraient simplement.

## Centralisé vs Décentralisé vs Distribué

![Image of Yaktocat](https://raw.githubusercontent.com/AbsoluteVirtueXI/alyra-courses/master/res/CDD.png)
Dans un réseau distribué, il n'y a pas de point d'autorité unique (ni même multiple).
L'objectif est d'éviter un point de défaillance unique: SPOF. Des mécanismes de consensus sont donc utilisés pour s'assurer que chaque noeud d'un réseau distribué fonctionne ensemble, et jamais de manière malveillante.
Dans le cas d'un réseau blockchain, des mécanismes de consensus sont utilisés pour contrôler comment une transaction blockchain peut-être validée et écrite dans un bloc puis exécutée.

## Mécanismes de consensus

### Le problème des généraux byzantins:

https://fr.wikipedia.org/wiki/Probl%C3%A8me_des_g%C3%A9n%C3%A9raux_byzantins

### Proof of work: PoW (ou preuve de travail en français)

Il s'agit de l'algorithme de consensus original. Avec le proof of work, les mineurs se font concurrence pour effectuer des transactions sur le réseau et ajouter de nouveaux blocs à la blockchain. Les mineurs doivent résoudre un casse-tête difficile en utilisant la puissance de traitement de leur ordinateur.
Le casse-tête mathématique à résoudre consiste à trouver un numéro de hash pour le header du bloc courant manipulant le champ nonce de ce bloc. Le numéro de hash à trouver doit être inférieur à un hash cible. Le hash cible est défini par une difficulté.

![Image of Yaktocat](https://raw.githubusercontent.com/AbsoluteVirtueXI/alyra-courses/master/res/bitcoin_block_hashing.jpg)
Le 1er mineur à résoudre le puzzle recoit une récompense pour son travail. Une preuve de travail est une donnée qui est difficile (coûteuse et longue) à produire mais facile à vérifier pour les autres et qui satisfait à certaines exigeances.

### Proof of stake: PoS (ou preuve d'enjeu / participation)

Le proof of stake est un type d'algorithme de consensus par lequel un réseau de blockchain de vise à attendre un consensus distribué. Dans les blockchains bassées sur le PoS, le créateur du bloc suivant est choisi via diverses combinaisons de sélection aléatoire et de richesse ou d'âge (c'est une mise). Dans le cas de la blockchain Ethereum, il y aura un seuil minimum de 32 ETH requis pour participer au jalonnement, et les validateurs devront exécuter un noeud de validation. Il n'est pas nécessaire que ce soit des machines spécialisées et cela peut-être fait sur un ordinateur grand public. Cependant, on s'attend à ce que les validateurs soient constamment en ligne ou encourent des sanctions mineurs.
Dans le cas de la blockchain exploitant exploitant un consensus PoS, les mineurs / validateurs / stakers peuvent extraire ou valider les transactions de bloc en fonction de la quantité de crypto-monnaies qu'ils détiennent. Pour ajouter un bloc malveillant, un attaquant devrait posséder 51% de toute la crypto-monnaie du réseau. Ethereum a historiquement exploité un consensus de Proof of Work. Cependant, l'une des raisons de passer à la Proof of Stake est qu'elle est généralement considérée comme beaucoup plus économe en énergie que la Proof of Work.

### Le Mining (minage en français)

Les noeuds miner créent des blocs dans la chaîne. Un bloc est une structure de données qui contient un ensemble de transactions. Lors de la création d'un bloc, le mineur sélectionnera certaines transactions dans son pool de transactions en attent (en attente d'être incluses dans la chaîne) et commencera à extraire le bloc. La chose importante à savoir est que l'exploitation minière est un processus coûteux. Par conséquent, si les mineurs n'obtenaient rien en échange de l'exploitation minière, personne ne le ferait. Dans Ethereum, lorsqu'un mineur extrait un nouveau bloc, il reçoit les frais de toutes les transections incluses dans ce bloc et une récompense de bloc (en fait 2 ETH). Par conséquent, plus le prix du gaz est élevé dans les transactions, plus les frais perçus par le mineur seront élevés.

### Fees/Gas (frais)

Les frais sur la blockchain Bitcoin, ou le système de gaz sur la blockchain Ethereum, sont des système de protection et une récompense pour les noeuds traitant la transaction. L'informatique coûte de l'argent: héberger un service stockant des informations de traitement de données. Chaque transaction que modifie un état dans une blockchain, comme l'envoi de crypto-monnaies, le déploiement d'un contrat intélligent ou la modification d'une valeur dans un contrat intelligent, coûtera des frais à l'expéditeur. Un autre aspect de la facturation de l'utilisateur pour ses actions sur le réseau est de prévenir les abus. Si vous payez pour chaque opération que vous exécutez, vous ferez de votre mieux pour implémenter votre code de la manière la plus efficace. Le coût des frais empêche également les mauvais acteurs d'inonder le système d'opérations inutiles (à moins qu'ils ne soient prêt à dépenser beaucoup d'argent pour exécuter du code inutile).

### Cryptographie asymétrique

Le cœur de la cryptographie asymétrique est l'utilisation de paires de clés publiques et privées. Une clé privée est un nombre aléatoire. La clé publique associée est un nombre généré par un algorithme unidirectionnel basé sur la clé privée. Cet algorithme est un algorithme de signature numérique à courbe elliptique (ecdsa). La courbe elliptique utilisée par Bitcoin, Ethereum et de nombreuses autres crypto-monnaies est appelée secp256k1. L'équation de la courbe secp256k1 est y² = x³ + 7. Cette courbe ressemble à:

![Image of Yaktocat](https://raw.githubusercontent.com/AbsoluteVirtueXI/alyra-courses/master/res/ecdsa.gif)

Une clé privée est une grande chaine de caractères, de préférence, généré de manière aléatoire. La clé privée doit être gardée secrète. Une clé publique est un grand nombre obtenu par un ecdsa sur la clé privée. La clé publique peut être partagée avec n'importe qui sans compromettre la sécurité de votre clé publique. Une adresse est obtenue à partir d'une clé publique avec une fonction de hachage. Une transaction contient le message de la transaction, et une signature de ce message générée avec la clé privée de l'expéditeur. N'importe qui peut vérifier la signature générée pour:

- récupérer la clé publique et l'adresse du signataire.
- vérifiez l'intégrité du message, qu'il s'agit du même message qui a été signé par le gisnataire.

Avec la signature et le hachage des données d'origine, nous pouvons effectuer une récupération de signature de courbe elliptique et obtenir la clé publique puis l'adresse. Si l'adresse récupérée est identique à l'adresse de l'expéditeur, alors le détenteur de la clé privée de la paire de clés publiques a bien signé le message.
