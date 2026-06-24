# Data Cleaning at 22 csv files

## Use Functions

- def df_info(df):
    summary = pd.DataFrame(df.info()) shape = df.shape size = df.size
    return summary, shape, size

df_info(df)

- def adult(df):
    summary = pd.DataFrame({
                'dtypes': df.dtypes,
                'nulls': df.isnull().sum(),
                'nulls_%': (df.isnull().mean() * 100).round(2),
                'nunique': df.nunique(),
                'sample': df.iloc[0]
              })
    return summary

adult(df)

def isnull(df): df['DepTime'] = df['DepTime'].fillna(df['DepTime'].mean()) df['ArrTime'] = df['ArrTime'].fillna(df['ArrTime'].mean()) df['ActualElapsedTime'] = df['ActualElapsedTime'].fillna(df['ActualElapsedTime'].mean()) df['ArrDelay'] = df['ArrDelay'].fillna(df['ArrDelay'].mean()) df['DepDelay'] = df['DepDelay'].fillna(df['DepDelay'].mean()) df['Distance'] = df['Distance'].fillna(0)

summary = pd.DataFrame({
    'null': df.isnull().sum(),
    'nulls_%': (df.isnull().mean() * 100).round(2)
})
return summary

isnull(df)

def drop_columns(df): columns = ['TailNum', 'SecurityDelay', "TaxiIn", 'TaxiOut', 'LateAircraftDelay', 'CancellationCode', 'CarrierDelay', 'NASDelay', 'WeatherDelay', 'AirTime'] df.drop(columns=columns, inplace=True) return adult(df)

drop_columns(df)

def duplicated(df): drop = df.duplicated().sum() df.drop_duplicates(inplace=True) return drop

duplicated(df)

def save_to_csv(df): df.to_csv('df_1992.csv', index=False, compression='gzip')

save_to_csv(df)
