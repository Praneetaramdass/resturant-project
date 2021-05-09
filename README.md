# resturant-project
#copying and keeping only data eastcoast and westcoast from 2015-2019
State_Keep= ['Nev.', 'N.Y.', 'Fla.', 'Mass.', 'Calif.']
resturant= y2015_2019[y2015_2019.State.isin(State_Keep)].copy()
resturant
#printing the amount of rows and columns in the copied data
print('The reduced dataframe has {0} rows and {1} columns'.format(resturant.shape[0], resturant.shape[1]))
#finding if there is missing data from any row or column from the copied data
print('Are there missing values? {}'.format(resturant.isnull().any().any()))


#finding the highest annual sales in $ of resturants from the extracted years and states 
df= resturant.pivot_table(index='Restaurant',values=['Sales','State'], aggfunc= max)
df.sort_values(by=['Sales'],inplace= True, ascending= False)
df

#showing in a chart what annual sales are like from 2015 to 2019 (pre covid) in states across the east and west coast
resturant.pivot_table('Sales', index='State', columns= 'Year', aggfunc= max)
