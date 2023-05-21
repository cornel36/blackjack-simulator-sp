import random

play_again = True

# 7 keep playing if player wants to
while play_again:
    # 1 Define the cards and their values
    card_values = {
        "2": 2,
        "3": 3,
        "4": 4,
        "5": 5,
        "6": 6,
        "7": 7,
        "8": 8,
        "9": 9,
        "10": 10,
        "J": 10,
        "Q": 10,
        "K": 10,
        "A": 11,
    }

    # 2 Create a deck
    ranks = ["2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K", "A"]
    suits = ["Hearts", "Diamonds", "Clubs", "Spades"]
    deck = []

    for suit in suits:
        for rank in ranks:
            card = (rank, suit)
            deck.append(card)

    # 3 Shuffle the deck
    shuffled_deck = deck.copy()
    random.shuffle(shuffled_deck)

    # 4 Deal the cards
    player_hand = []
    dealer_hand = []

    player_hand.append(shuffled_deck.pop())
    dealer_hand.append(shuffled_deck.pop())
    player_hand.append(shuffled_deck.pop())
    dealer_hand.append(shuffled_deck.pop())

    # 5 Calculate hand value
    def calculate_hand_value(hand):
        hand_value = 0
        num_aces = 0

        for card in hand:
            rank = card[0]
            value = card_values[rank]
            hand_value += value

            if rank == "A":
                num_aces += 1

        # 5.1 Change the Aces value if needed
        while hand_value > 21 and num_aces > 0:
            hand_value -= 10
            num_aces -= 1

        return hand_value

    # 6 Game loop
    game_over = False

    while not game_over:
        print("Player:", player_hand)
        print("Dealer:", dealer_hand)

        player_decision = input("Hit or stand (h/s)? ")

        if player_decision.lower() == "h":
            player_hand.append(shuffled_deck.pop())
            player_value = calculate_hand_value(player_hand)
            if player_value > 21:
                print("Player:", player_hand)
                print("Dealer:", dealer_hand)
                print("Player busts. Dealer wins!")
                game_over = True

        elif player_decision.lower() == "s":
            dealer_value = calculate_hand_value(dealer_hand)
            player_value = calculate_hand_value(player_hand)

            while dealer_value < 17:
                dealer_hand.append(shuffled_deck.pop())
                dealer_value = calculate_hand_value(dealer_hand)

            if dealer_value > 21:
                print("Player:", player_hand)
                print("Dealer:", dealer_hand)
                print("Dealer busts. Player wins!")
            elif dealer_value > player_value:
                print("Player:", player_hand)
                print("Dealer:", dealer_hand)
                print("Dealer wins!")
            elif dealer_value < player_value:
                print("Player:", player_hand)
                print("Dealer:", dealer_hand)
                print("Player wins!")
            else:
                print("Player:", player_hand)
                print("Dealer:", dealer_hand)
                print("It's a tie!")

            game_over = True
        else:
            print("Invalid input. Enter 'h' to hit or 's' to stand.")

    play_again_input = input("Do you want to play again? (y/n): ")
    if play_again_input.lower() != "y":
        play_again = False

print("Thanks for playing!")
