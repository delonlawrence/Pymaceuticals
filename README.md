# Pymaceuticals
This part of the code is from chat

capomulin_data = df[df['Drug Regimen'] == 'Capomulin']

capomulin_mouse_data = capomulin_data.groupby('Mouse ID')[['Weight (g)', 'Tumor Volume (mm3)']].mean(numeric_only=True)

correlation = round(st.pearsonr(capomulin_mouse_data['Weight (g)'], capomulin_mouse_data['Tumor Volume (mm3)'])[0], 2)

slope, intercept, rvalue, pvalue, stderr = st.linregress(capomulin_mouse_data['Weight (g)'], capomulin_mouse_data['Tumor Volume (mm3)'])

regress_values = slope * capomulin_mouse_data['Weight (g)'] + intercept

plt.scatter(capomulin_mouse_data['Weight (g)'], capomulin_mouse_data['Tumor Volume (mm3)'])

plt.plot(capomulin_mouse_data['Weight (g)'], regress_values, color='red')

plt.xlabel('Weight (g)')
plt.ylabel('Average Tumor Volume (mm3)')
plt.title('Mouse Weight vs Average Tumor Volume (Capomulin)')
plt.text(20, 35, f"Correlation coefficient: {correlation}")






