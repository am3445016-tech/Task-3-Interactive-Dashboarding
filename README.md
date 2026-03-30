# Task-3-Interactive-Dashboarding

AOV = df['Final_Amount'].mean()
Total_Revenue = df['Final_Amount'].sum()
Conversion_Rate = len(df) / df['Website_Visits'].sum()
high_value_rate = df['High_Value_Customer'].mean() * 100
avg_shipping = df['Shipping_Days'].mean()
df['Customer_Segment'] = pd.qcut(
    df['Final_Amount'],
    q=3,
    labels=['Low Value', 'Medium Value', 'High Value']
)
df['Engagement_Level'] = pd.qcut(
    df['Website_Visits'],
    q=3,
    labels=['Low Engagement', 'Medium Engagement', 'High Engagement']
)
df['Customer_Segment'].value_counts()
df.groupby('Customer_Segment')['Final_Amount'].sum()
df.groupby('Customer_Segment')['Final_Amount'].mean()
segment_analysis = df.groupby(
    ['Customer_Segment', 'Engagement_Level']
)['Final_Amount'].mean()

segment_analysis
import matplotlib.pyplot as plt
df['Customer_Segment'].value_counts().plot(kind='bar')
plt.title("Customer Segments Distribution")
plt.show()
df.groupby('Customer_Segment')['Final_Amount'].sum().plot(kind='bar')
plt.title("Revenue Contribution by Segment")
plt.show()
df.groupby('Customer_Segment')['High_Value_Customer'].mean()
