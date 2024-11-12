def get_player_stats(player_id):
    query = f"SELECT * FROM Performance WHERE player_id = {player_id}"
    cursor.execute(query)
    return cursor.fetchall()
    def calculate_goals_per_game(player_id):
    stats = get_player_stats(player_id)
    total_goals = sum(row[2] for row in stats)  # Assuming goals are in column 2
    total_games = len(stats)
    return total_goals / total_games if total_games > 0 else 0
    mport matplotlib.pyplot as plt

def plot_goals_over_time(player_id):
    stats = get_player_stats(player_id)
    dates = [row[1] for row in stats]  # Assuming date is in column 1
    goals = [row[2] for row in stats]
    
    plt.plot(dates, goals, marker='o')
    plt.xlabel("Date")
    plt.ylabel("Goals")
    plt.title("Goals Over Time")
    plt.show()
