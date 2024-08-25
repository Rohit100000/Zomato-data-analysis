# Zomato Data Analysis

Welcome to the Zomato Data Analysis project! This analysis explores various aspects of restaurant data from Zomato, using Python libraries such as Pandas, NumPy, Matplotlib, and Seaborn. The goal is to uncover insights into restaurant ratings, types, and customer preferences.

## Project Overview

In this project, we analyze a dataset of Zomato restaurants to:

- Explore the distribution of restaurant types.
- Examine the relationship between restaurant ratings and other factors.
- Visualize various patterns and trends in the data.

## Getting Started

To get started with this project, follow these steps:

### 1. Clone the Repository

First, clone the repository to your local machine:

```bash
git clone https://github.com/yourusername/zomato-data-analysis.git
cd zomato-data-analysis
```

### 2. Install Dependencies

Ensure you have the required libraries installed. You can set up a virtual environment and install the dependencies using:

```bash
python -m venv venv
source venv/bin/activate  # Use `venv\Scripts\activate` on Windows
pip install pandas numpy matplotlib seaborn
```

### 3. Prepare the Data

Place the Zomato dataset file (`Zomato data.csv`) in the project directory. The dataset should include the following columns:

- `name`
- `online_order`
- `book_table`
- `rate`
- `votes`
- `approx_cost(for two people)`
- `listed_in(type)`

### 4. Run the Analysis

Execute the provided Python scripts to perform the analysis:

```bash
python analyze_data.py
```

## Analysis Details

Here’s a summary of the analysis performed:

### Data Loading and Cleaning

We start by loading the dataset and checking for missing values. The data is then cleaned and prepared for analysis.

### Exploratory Data Analysis (EDA)

1. **Restaurant Type Distribution**: We use a count plot to visualize the distribution of different types of restaurants (e.g., Cafes, Buffets, Dining).

   ```python
   sns.countplot(x=df["listed_in(type)"])
   plt.xlabel("Type of Restaurant")
   plt.show()
   ```

   **Conclusion**: The majority of restaurants fall into the Dining category.

2. **Votes by Restaurant Type**: We aggregate the total votes received by each type of restaurant and visualize it.

   ```python
   grouped_data = df.groupby("listed_in(type)")["votes"].sum()
   plt.plot(grouped_data, c="green", marker="o")
   plt.xlabel("Type of Restaurant", color="red", size=20)
   plt.ylabel("Votes", color="red", size=20)
   plt.show()
   ```

   **Conclusion**: Dining restaurants have received the highest number of votes.

3. **Rating Distribution**: We plot a histogram to understand the distribution of restaurant ratings.

   ```python
   plt.hist(df["rate"], bins=8)
   plt.title("Rating Distribution")
   plt.show()
   ```

   **Conclusion**: Most restaurants have ratings between 3.5 and 4.

4. **Average Spending**: We examine the approximate cost for two people at restaurants to see common spending patterns.

   ```python
   sns.countplot(x=df["approx_cost(for two people)"])
   plt.xlabel("Approximate Cost for Two People")
   plt.show()
   ```

   **Conclusion**: The majority of couples prefer restaurants with an approximate cost of 2300 rupees.

5. **Online vs. Offline Ratings**: We compare ratings for restaurants that offer online ordering versus those that do not.

   ```python
   sns.boxplot(x="online_order", y="rate", data=df)
   plt.xlabel("Online Order")
   plt.ylabel("Rating")
   plt.show()
   ```

   **Conclusion**: Restaurants offering online ordering tend to receive higher ratings compared to those that do not.

6. **Heatmap of Orders by Restaurant Type**: We use a heatmap to visualize the distribution of online and offline orders across different restaurant types.

   ```python
   pivot_table = df.pivot_table(index="listed_in(type)", columns="online_order", aggfunc="size", fill_value=0)
   sns.heatmap(pivot_table, annot=True, cmap="YlGnBu", fmt="d")
   plt.title("Heatmap of Orders by Restaurant Type")
   plt.xlabel("Online Order")
   plt.ylabel("Restaurant Type")
   plt.show()
   ```

   **Conclusion**: Dining restaurants primarily accept offline orders, whereas cafes mostly receive online orders.

## Project Structure

- `analyze_data.py` - Script to perform data analysis and generate visualizations.
- `Zomato data.csv` - Dataset file containing restaurant information.

## Contributing

We welcome contributions to enhance this project! To contribute:

1. Fork the repository.
2. Create a new branch for your feature or fix.
3. Commit your changes and push to your branch.
4. Open a Pull Request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For any questions or feedback, feel free to reach out to [your email].

---

Feel free to modify any details to better fit your project or preferences!
