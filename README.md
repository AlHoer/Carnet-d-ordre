<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> Projet Carnet d'Ordre </title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background-color: #f4f4f4;
            color: #333;
        }
        .container {
            background: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 2px 4px rgba(0,0,0,.1);
            margin: 20px 0;
        }
        h1, h2, h3 {
            color: #0056b3;
        }
        h2 {
            border-bottom: 2px solid #eee;
            padding-bottom: 5px;
        }
        p, ul {
            line-height: 1.6;
        }
        ul {
            padding-left: 20px;
        }
        code {
            background-color: #eee;
            padding: 2px 4px;
            border-radius: 4px;
            font-family: monospace;
        }
        .footer {
            text-align: center;
            margin-top: 20px;
            font-size: 0.8em;
            color: #777;
        }
    </style>
</head>
<body>

<div class="container">
   <section id="creation-dun-carnet-dordre" class="level1">
<h1>Création d'un carnet d'ordre</h1>
<hr>
<section id="1.---Analyse-et-Conception-Révisée" class="level2">
<h2 class="anchored" data-anchor-id="1.---Analyse-et-Conception-Révisée">1. Analyse et Conception Révisée</h2>
<section id="a.--Compréhension-Approfondie-des-Carnets-dOrdres" class="level3">
<h3 class="anchored" data-anchor-id="a.--Compréhension-Approfondie-des-Carnets-dOrdres">a. Compréhension Approfondie des Carnets d'Ordres</h3>
  
<p> Les carnets d'ordres doivent fonctionner de manière continue, reflétant un environnement dynamique où les participants peuvent à tout moment ajouter ou annuler des ordres. Cette flexibilité est essentielle pour simuler fidèlement le comportement des marchés financiers réels. Le projet que nous avons réalisé a pour but de créer un carnet d’ordres qui va être fonctionnel que cela soit pour stocker, exécuter, chercher ou même créer un ordre d’achat ou de vente. Il contient deux classes principales, la première est celle de la configuration qui va avoir pour objectif de créer un carnet d’ordre et de lui permettre de s’auto-gérer parfaitement. La seconde classe correspond à la création d’une interface qui va permettre à l’utilisateur de gérer directement le carnet d’ordre. Nous allons donc vous expliquer notre code étape par étape <p>

<section id="b.-Mise-en-Avant-des-Concepts-de-Maker-et-Taker" class="level3">
<h3 class="anchored" data-anchor-id="b.-Mise-en-Avant-des-Concepts-de-Maker-et-Taker">b. Mise en Avant des Concepts de Maker et Taker</h3>  
  
<p>- Maker : Les Makers ajoutent de la liquidité au marché en plaçant des ordres qui ne sont pas exécutés immédiatement, restant dans le carnet jusqu'à ce qu'un prix correspondant soit trouvé.</p>
<p>- Taker : Les Takers retirent de la liquidité en exécutant des ordres contre les ordres existants dans le carnet, facilitant ainsi des transactions immédiates.</p>
<p>Ces rôles influencent directement la dynamique de l'offre et de la demande et seront essentiels pour simuler le fonctionnement du marché.</p>

<section id="c.-Intégration-des-Notions-de-Tick-et-Lot" class="level3">
<h3 class="anchored" data-anchor-id="c.-Intégration-des-Notions-de-Tick-et-Lot">c. Intégration des Notions de Tick et Lot</h3>
  
<p>- Tick : Le Tick représente le plus petit mouvement de prix possible pour un actif. Cette notion est cruciale pour déterminer comment les prix peuvent évoluer dans le carnet d'ordres.</p>
<p>- Lot : Le Lot dénote la quantité minimale ou un multiple de cette quantité qu'un actif peut être échangé. Cette règle affecte la façon dont les ordres sont placés et exécutés.</p>

<section id="Hypothèses-de-Construction-Révisées" class="level2">
    <h2 class="anchored" data-anchor-id="Hypothèses-de-Construction-Révisées">Hypothèses de Construction Révisées</h2>
    <p>1. Continuité et Flexibilité : Le simulateur gérera les ordres de manière continue, permettant à tout moment l'ajout et l'annulation d'ordres pour simuler un environnement de marché dynamique.</p>
    <p>2. Rôles Dynamiques de Maker et Taker : Le simulateur reconnaîtra et distinguera les actions des Makers et des Takers pour refléter leur impact sur la liquidité du marché.</p>
    <p>3. Respect des Contraintes de Tick et Lot : Les règles concernant les Ticks et les Lots sont intégrés à l'aide d'un bouton qui renvoie les valeurs à respecter pour l'utilisateur.</p>
</section>
<section id="Entités-Clés-et-Structure-de-Données" class="level2">
    <h2 class="anchored" data-anchor-id="Entités-Clés-et-Structure-de-Données">Entités Clés et Structure de Données</h2>
    <p>- Classe 'Ordre' : Représente un ordre dans le carnet avec des attributs pour le type d'ordre, le prix, la quantité, et l'identifiant du participant. Cette classe tiendra compte des notions de Tick et Lot pour valider les ordres.</p>
    <p>- Classe 'CarnetOrdres' : Gère un ensemble d'ordres d'achat et de vente, en permettant leur ajout, leur annulation, et en fournissant une visualisation claire du carnet. Cette classe gérera également la distinction entre les ordres de Makers et de Takers pour simuler l'impact sur la liquidité.</p>
</section>
<section id="Conclusion-et-Prochaine-Étape" class="level2">
    <h2 class="anchored" data-anchor-id="Conclusion-et-Prochaine-Étape">Conclusion et Prochaine Étape</h2>
    <p>La prochaine étape consistera à détailler le développement de la classe CarnetOrdres et à simuler son fonctionnement dans un environnement de marché.</p>
</section>
</section>

<section id="Développement-de-la-Classe-CarnetOrdres" class="level1">
    <h1>Développement de la Classe CarnetOrdres</h1>
    <hr>
    <section id="Structure-de-la-Classe" class="level2">
        <h2 class="anchored" data-anchor-id="Structure-de-la-Classe">a. Structure de la Classe</h2>
        <p>La classe CarnetOrdres sera structurée pour gérer efficacement les ordres d'achat et de vente. Cette partie du code crée la classe CarnetOrdres, qui est le cœur de notre application de gestion des ordres. Lors de son initialisation, elle établit une connexion avec l'interface utilisateur (self.gui) pour permettre une interaction fluide entre la logique métier et l'interface graphique. Les variables self.ordres_achat et self.ordres_vente servent à stocker respectivement les ordres d'achat et de vente. Ces listes sont des conteneurs pour les données des ordres, telles que leur prix, leur quantité et leur identifiant. La liste self.transactions est destinée à enregistrer les transactions effectuées sur le marché. Chaque transaction est représentée sous forme de dictionnaire, capturant des détails tels que l'identifiant de l'ordre d'achat et de vente, ainsi que le prix et la quantité échangés. L'appel à self.lire_ordres(...) suggère l'existence d'une fonction pour charger les données initiales du carnet d'ordres à partir d'un fichier. Cela garantit que le carnet d'ordres est prérempli avec des données significatives au démarrage de l'application. Enfin, self.auto_executing est un indicateur booléen qui contrôle le mode continu de l'application. Lorsqu'il est activé, les ordres sont automatiquement exécutés à intervalles réguliers, offrant une fonctionnalité essentielle pour les traders qui souhaitent automatiser leurs transactions. </p>
        <pre><code class="language-python">class CarnetOrdres:
       import tkinter as tk
    from tkinter import ttk
    import tkinter.messagebox
    import random
    import time
    
    
    class CarnetOrdres:
        def __init__(self, gui):
            self.gui = gui
            self.ordres_achat = []
            self.ordres_vente = []
            self.transactions = []
            self.lire_ordres('/Users/albanhoerdt/Documents/Cours Dauphine/L3/S2/Python/Projet/Donnees_OrderBook')
            self.auto_executing = False  # Variable pour activer/désactiver le mode continu
</code></pre>
    </section>
    <section id="Gestion-des-Ordres" class="level2">
        <h2 class="anchored" data-anchor-id="Gestion-des-Ordres">b. Gestion des Ordres</h2>
        <p>Cette fonction, toggle_auto_executing, est une pièce essentielle de notre application de gestion des ordres. Voici un résumé de son fonctionnement. Elle permet de basculer entre l'activation et la désactivation du mode d'exécution automatique des ordres. Lorsqu'elle est appelée, elle inverse simplement l'état actuel du mode automatique en basculant la valeur de self.auto_executing. Si le mode était activé, il serait désactivé et vice versa. Si le mode automatique est activé (self.auto_executing est True), la fonction effectue deux actions importantes. Elle appelle self.execute_continuously(), une méthode chargée d'exécuter les ordres en continu à intervalles réguliers, assurant ainsi que les transactions sont traitées en temps réel. Elle lance également immédiatement self.generate_orders_periodically(), une méthode destinée à démarrer la génération périodique de nouveaux ordres. Cela peut être utile pour assurer un flux constant d'ordres dans l'application. En revanche, si le mode automatique est désactivé, la fonction ne prend aucune action supplémentaire, mais elle pourrait être étendue à l'avenir pour inclure des fonctionnalités d'arrêt du processus, comme indiqué par le commentaire.</p>
    </section>
    <section id="Activation-mode-continu" class="level2">
        <h2 class="anchored" data-anchor-id="Activation-mode-continu">c. Activation mode continu </h2>
        <pre><code class="language-python"> def toggle_auto_executing(self):
        self.auto_executing = not self.auto_executing
        if self.auto_executing:
            self.execute_continuously()
            self.generate_orders_periodically()  # Appel immédiat pour démarrer la génération des ordres
        else:
            # Ajouter des mesures pour arrêter le processus si nécessaire
            pass
</code></pre>
    </section>
    <section id="Méthode-continu" class="level3">
        <h2 class="anchored" data-anchor-id="Méthode-continu">Méthode continu</h2>
        <p>On a ensuite la méthode, execute_continuously, assure une exécution continue des ordres à intervalles réguliers tant que le mode d'exécution automatique est activé. Elle vérifie d'abord si le mode automatique est activé. Si tel est le cas, elle lance l'exécution des ordres en appelant la méthode executer_ordres(). Ensuite, elle utilise self.gui.master.after(1000, self.execute_continuously) pour planifier un rappel de la méthode après une seconde (1000 millisecondes), assurant ainsi une exécution périodique des ordres. Ce processus se poursuit tant que le mode automatique reste activé, garantissant un flux continu d'activité de trading dans notre application.</p>
    <pre><code class="language-python">def execute_continuously(self):
        if self.auto_executing:
            self.executer_ordres()
            self.gui.master.after(1000, self.execute_continuously)
    </code></pre>
    </section>
</section>

<section id="Lecture-des-ordres" class="level2">
    <h1>Lecture des ordres</h1>
    <hr>
    <section id="Méthode-lire_ordres" class="level2">
        <h2 class="anchored" data-anchor-id="Méthode-lire_ordres">a. Méthode lire_ordres</h2>
        <p>La méthode lire_ordres est une fonction clé de notre système de gestion d'ordres. Elle ouvre le fichier spécifié, parcourt ses lignes et extrait les détails de chaque ordre, limitant la lecture à 40 ordres maximum. Pour chaque ligne, elle détermine le type d'ordre (achat ou vente), l'identifiant, la référence de l'actif, le prix et la quantité. Ces données sont utilisées pour ajouter les ordres au carnet d'ordres via la méthode ajouter_ordre, garantissant que l'application démarre avec un ensemble initial d'ordres prêts à être traités. Ainsi, cette méthode assure un chargement efficace des données d'ordres, élément crucial pour le bon fonctionnement de notre système de trading.</p>
    </section>
    <section <pre><code class="language-python">def lire_ordres(self, filepath):
        with open(filepath, 'r') as file:
            for i, line in enumerate(file):
                if i >= 40:
                    break
                parts = line.strip().split(',')
                type_ordre = 'achat' if parts[0] == 'B' else 'vente'
                id_ordre = int(parts[1])
                ref_actif = parts[2].strip('"')
                prix = float(parts[3])
                quantite = int(parts[4]) if len(parts) > 4 else 1
                self.ajouter_ordre(type_ordre, id_ordre, ref_actif, prix, quantite)
    </code></pre>
    </section>
</section>

<section id="Génération-des-taker-et-des-order" class="level2">
    <h1>Génération des taker et des order</h1>
    <hr>
    <section id="Méthode-taker" class="level2">
        <h2 class="anchored" data-anchor-id="Méthode-taker">a. Méthode taker</h2>
        <p>La méthode generate_taker_order crée des ordres de type "taker" de manière aléatoire pour simuler des transactions sur le marché. Elle choisit aléatoirement une référence d'actif parmi une liste prédéfinie et détermine aléatoirement si l'ordre sera un achat ou une vente. Si c'est un achat et qu'il existe des ordres de vente disponibles, il fixe le prix d'achat légèrement au-dessus du minimum du marché et génère une quantité aléatoire. Ensuite, il ajoute cet ordre au carnet d'ordres. Si le mode d'exécution automatique est activé, il exécute immédiatement les ordres ajoutés. De même, s'il s'agit d'une vente et qu'il existe des ordres d'achat disponibles, il fixe le prix de vente légèrement en dessous du maximum du marché et génère une quantité aléatoire, puis ajoute cet ordre au carnet d'ordres. Encore une fois, s'il est en mode d'exécution automatique, il exécute immédiatement les ordres ajoutés. Cette méthode simule la prise de décision aléatoire des acteurs sur le marché et leur interaction en générant des ordres de taker basés sur des conditions aléatoires prédéfinies.</p>
    </section>
    <pre><code class="language-python">def generate_taker_order(self):
        reference = random.choice(['30501', '31601', '31502'])
        order_type = random.choice(['achat', 'vente'])
        if order_type == 'achat' and self.ordres_vente:
            # Taker achète à un prix légèrement supérieur au minimum du marché
            prix_achat = max((ordre['prix'] for ordre in self.ordres_vente), default=10) + random.uniform(1, 100)
            prix_achat = round(prix_achat, 1)
            quantite_achat = random.randint(1, 2000)
            self.ajouter_ordre('achat', len(self.ordres_achat) + 1, reference, prix_achat, quantite_achat)
            if self.auto_executing:  # Exécute les ordres immédiatement si en mode continu
                self.executer_ordres()
        elif order_type == 'vente' and self.ordres_achat:
            # Taker vend à un prix légèrement inférieur au maximum du marché
            prix_vente = min((ordre['prix'] for ordre in self.ordres_achat), default=10) - random.uniform(1, 100)
            prix_vente = round(prix_vente, 1)
            quantite_vente = random.randint(1, 2000)
            self.ajouter_ordre('vente', len(self.ordres_vente) + 1, reference, prix_vente, quantite_vente)
            if self.auto_executing:  # Exécute les ordres immédiatement si en mode continu
                self.executer_ordres()
    </code></pre>
    <section id="Méthode-maker" class="level2">
        <h2 class="anchored" data-anchor-id="Méthode-maker">b. Méthode maker</h2>
        <p>La méthode generate_maker_order crée des ordres de type "maker" de manière aléatoire pour simuler des transactions sur le marché, elle est quasiment similaire à la méthode précédente, du moins sur le fonctionnement. Elle sélectionne aléatoirement une référence d'actif parmi une liste prédéfinie et détermine aléatoirement si l'ordre sera un achat ou une vente. Si c'est un achat et qu'il existe des ordres de vente disponibles, elle fixe le prix d'achat légèrement en dessous du minimum du marché et génère une quantité aléatoire. Ensuite, elle ajoute cet ordre au carnet d'ordres. Si le mode d'exécution automatique est activé, elle exécute immédiatement les ordres ajoutés. De même, si c'est une vente et qu'il existe des ordres d'achat disponibles, elle fixe le prix de vente légèrement au-dessus du maximum du marché, génère une quantité aléatoire, puis ajoute cet ordre au carnet d'ordres. Encore une fois, si le mode d'exécution automatique est activé, elle exécute immédiatement les ordres ajoutés. Cette méthode simule le comportement des acteurs du marché qui ajoutent des liquidités en créant des ordres de maker basés sur des conditions aléatoires prédéfinies.</p>
        <pre><code class="language-python">def generate_maker_order(self):
        reference = random.choice(['30501', '31601', '31502'])
        order_type = random.choice(['achat', 'vente'])
        if order_type == 'achat' and self.ordres_vente:
            # Maker achète à un prix légèrement inférieur au minimum du marché
            prix_achat = min((ordre['prix'] for ordre in self.ordres_vente), default=10) - random.uniform(1, 100)
            prix_achat = round(prix_achat, 1)
            quantite_achat = random.randint(1, 2000)
            self.ajouter_ordre('achat', len(self.ordres_achat) + 1, reference, prix_achat, quantite_achat)
            if self.auto_executing:  # Exécute les ordres immédiatement si en mode continu
                self.executer_ordres()
        elif order_type == 'vente' and self.ordres_achat:
            # Maker vend à un prix légèrement supérieur au maximum du marché
            prix_vente = max((ordre['prix'] for ordre in self.ordres_achat), default=10) + random.uniform(1, 100)
            prix_vente = round(prix_vente, 1)
            quantite_vente = random.randint(1, 2000)
            self.ajouter_ordre('vente', len(self.ordres_vente) + 1, reference, prix_vente, quantite_vente)
            if self.auto_executing:  # Exécute les ordres immédiatement si en mode continu
                self.executer_ordres()
</code></pre>
    </section>
    <section id="Méthode-ajouter_ordre" class="level1">
        <h2 class="anchored" data-anchor-id="Méthode-ajouter_ordre">Méthode ajouter_ordre</h2>
        <p>La méthode ajouter_ordre gère l'ajout d'un nouvel ordre au carnet d'ordres. Elle prend en paramètres le type d'ordre (achat ou vente), l'identifiant de l'ordre, la référence de l'actif, le prix et la quantité. Avant d'ajouter l'ordre, elle normalise le type d'ordre en le mettant en minuscules. Ensuite, elle détermine le numéro d'ordre suivant en trouvant le maximum des identifiants d'ordres existants dans les listes d'ordres d'achat et de vente, puis elle incrémente ce numéro. Si la quantité de l'ordre est supérieure à zéro, elle crée un dictionnaire représentant l'ordre avec les détails fournis. Selon le type d'ordre, elle ajoute cet ordre à la liste appropriée (achat ou vente), trie ensuite les listes par identifiant d'ordre, et met à jour l'affichage du carnet d'ordres dans l'interface graphique. Cette méthode assure donc l'ajout correct et la mise à jour des ordres dans le carnet d'ordres, maintenant ainsi une représentation précise et à jour de l'état du marché.</p>
         <pre><code class="language-python"> def ajouter_ordre(self, type_ordre, id_ordre, ref_actif, prix, quantite):
        type_ordre = type_ordre.lower()

        max_order_number = max(
            max((ordre['id_ordre'] for ordre in self.ordres_achat), default=0),
            max((ordre['id_ordre'] for ordre in self.ordres_vente), default=0)
        )
        next_order_number = max_order_number + 1

        if quantite > 0:
            ordre = {'type': type_ordre, 'id_ordre': next_order_number, 'ref_actif': ref_actif, 'prix': prix, 'quantite': quantite}
            if type_ordre == 'achat':
                self.ordres_achat.append(ordre)
                self.ordres_achat.sort(key=lambda x: x['id_ordre'])
            else:
                self.ordres_vente.append(ordre)
                self.ordres_vente.sort(key=lambda x: x['id_ordre'])
            self.gui.afficher_carnet(self.ordres_achat, self.ordres_vente)
         </code></pre>
    </section>
</section>

<section id="Exécution-des-ordres" class="level1">
    <h1>Exécution des ordres</h1>
    <hr>
    <section id="Méthode-exécution-logique" class="level2">
        <h2 class="anchored" data-anchor-id="Méthode-exécution-logique">a. Méthode exécution logique</h2>
        <p>La méthode executer_ordres_logique prend en charge la logique d'exécution des ordres dans le carnet d'ordres. Elle commence par trier les listes d'ordres d'achat et de vente en fonction du prix, les achats par ordre décroissant et les ventes par ordre croissant. Ensuite, elle parcourt les listes pour trouver les transactions possibles en comparant les prix et les références d'actif des ordres. Si une transaction est possible, elle détermine la quantité à exécuter, enregistre la transaction dans l'historique des transactions, met à jour les quantités des ordres impliqués et supprime les ordres épuisés. Après avoir traité toutes les transactions possibles, elle met à jour l'affichage du carnet d'ordres dans l'interface graphique et ouvre une fenêtre affichant l'historique des transactions. Cette méthode assure l'exécution correcte des ordres en fonction de leur prix et de leur quantité, tout en maintenant un suivi précis des transactions effectuées.</p>
        <pre><code class="language-python"> def executer_ordres_logique(self):
        achats = sorted(self.ordres_achat[:], key=lambda x: x['prix'], reverse=True)
        ventes = sorted(self.ordres_vente[:], key=lambda x: x['prix'])
        for achat in achats:
            if achat['quantite'] == 0:
                continue
            for vente in ventes:
                if vente['quantite'] == 0:
                    continue
                if achat['ref_actif'] == vente['ref_actif'] and achat['prix'] >= vente['prix']:
                    quantite_executee = min(achat['quantite'], vente['quantite'])
                    transaction_prix = vente['prix']
                    self.transactions.append({
                        'achat_id': achat['id_ordre'],
                        'vente_id': vente['id_ordre'],
                        'prix': transaction_prix,
                        'quantite': quantite_executee,
                        'ref_actif': achat['ref_actif']
                    })
                    achat['quantite'] -= quantite_executee
                    vente['quantite'] -= quantite_executee
                    if vente['quantite'] == 0:
                        self.ordres_vente.remove(vente)
                    if achat['quantite'] == 0:
                        self.ordres_achat.remove(achat)
                        break
        self.gui.afficher_carnet(self.ordres_achat, self.ordres_vente)
        self.gui.ouvrir_historique(self.transactions)
</code></pre>
    </section>
    <section id="Exécution" class="level2">
        <h2 class="anchored" data-anchor-id="Exécution">b. Exécution</h2>
        <p>La méthode executer_ordres est responsable de l'exécution des ordres. Elle commence par appeler la méthode executer_ordres_logique pour gérer la logique d'exécution des ordres. Ensuite, elle met à jour l'affichage du carnet d'ordres dans l'interface graphique en affichant les listes d'ordres d'achat et de vente mises à jour. Enfin, elle ouvre une fenêtre affichant l'historique des transactions. Cette méthode coordonne le processus d'exécution des ordres et assure la mise à jour de l'affichage de l'état du carnet d'ordres et de l'historique des transactions.</p>
    <pre><code class="language-python">     
    def executer_ordres(self):
        self.executer_ordres_logique()
        self.gui.afficher_carnet(self.ordres_achat, self.ordres_vente)
        self.gui.ouvrir_historique(self.transactions)
    </code></pre>
    </section>
</section>

<section id="Détermination-des-tick-et-des-lot" class="level1">
    <h1>Détermination des ticks et des lots</h1>
    <hr>
    <section id="Méthode-calculer_tick_et_lot" class="level2">
        <h2 class="anchored" data-anchor-id="Méthode-calculer_tick_et_lot">a. Méthode calculer_tick_et_lot</h2>
        <p>La fonction calculer_tick_et_lot prend en entrée une référence d'actif et cherche ses données de tick et de lot dans un fichier spécifié, ici Donnees_Tick_Lot. Elle ouvre le fichier, parcourt chaque ligne, et sépare les éléments en parties. Si la référence d'actif correspond à celle trouvée dans une ligne du fichier, la fonction extrait les valeurs du tick et du lot associé à cette référence. Ensuite, elle retourne ces valeurs. Si aucune correspondance n'est trouvée, elle retourne "N/A" pour indiquer que les données n'ont pas été trouvées. Cette fonction récupère les informations sur le tick et le lot d'un actif à partir d'un fichier et les renvoie pour utilisation.</p>
    <pre><code class="language-python"> def calculer_tick_et_lot(self, ref_actif):
        filepath = "/Users/albanhoerdt/Documents/Cours Dauphine L3/S2/Python/Projet/Donnees_Tick_Lot"
        with open(filepath, 'r') as file:
            for line in file:
                parts = line.strip().split(',')
                if parts[0] == ref_actif:
                    lot = float(parts[1])
                    tick = float(parts[2])
                    return tick, lot
        return "N/A", "N/A"
    </code></pre>
    </section>
    <section id="Seconde-Classe-CarnetOrdresGUI" class="level1">
        <h2 class="anchored" data-anchor-id="Seconde-Classe-CarnetOrdresGUI">b. Seconde Classe CarnetOrdresGUI</h2>
        <p>Dans la seconde classe CarnetOrdresGUI nous allons créer l’interface, en voici un aperçu, nous expliquons dans la suite sa création et son utilisation.</p>
        <img width="495" alt="Capture d’écran 2024-04-26 à 20 28 33" src="https://github.com/AlHoer/Carnet-d-ordre/assets/163281343/1663689a-e5c4-43ba-9aae-a94b4194f673">
     <section id="Code-de-la-Classe-CarnetOrdresGUI" class="level2">
        <h2 class="anchored" data-anchor-id="Code-de-la-Classe-CarnetOrdresGUI"> Code de la Classe CarnetOrdresGUI</h2>
    <pre><code class="language-python">class CarnetOrdresGUI:
    def __init__(self, master):
        self.master = master
        master.title("Carnet d'ordres")
        self.setup_trees()
        self.setup_form()
    </code></pre>
    </section>
</section>
</div>

<div class="footer">
    Projet Carnet d'Ordre - Développé par [Votre Nom]
</div>

</body>
</html>
