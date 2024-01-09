# import requests
import pandas as pd
from bs4 import BeautifulSoup
import json
import re

##########################_ICC_____T20-TEAM_____RANKING_##########################

url = "https://www.icc-cricket.com/rankings/mens/team-rankings/t20i"

r = requests.get(url)

soup = BeautifulSoup(r.text, "lxml")

header_dict = {}
result_dict = {}
header_list = []
matches_dict = {}
matches_list = []
names = soup.find("div", class_ = "rankings-block__title-container").text
names1 = soup.find("div", class_ = "rankings-table__last-updated").text

result_dict["title"] =  re.sub('\s+',' ',names)
result_dict["last_update"] = re.sub('\s+',' ',names1 )

# print(names, names1.replace("(GMT)",""))


names2 = soup.find("tbody")
comman_th_list = names2.find("tr",class_ = "rankings-block__banner").findAll("td")

matches_dict["pos"]  = re.sub('\s+',' ',comman_th_list[0].text)
matches_dict["team"] =  re.sub('\s+',' ',comman_th_list[1].findAll("span")[1].text)
matches_dict["match"] = re.sub('\s+',' ',comman_th_list[2].text)
matches_dict["points"]  = re.sub('\s+',' ',comman_th_list[3].text)
matches_dict["rating"] =  re.sub('\s+',' ',comman_th_list[4].text)

matches_list.append(matches_dict)
names3 = names2.findAll("tr", class_ = "table-body")


for i in names3:
    matches_dict = {}
    common_td_list = i.findAll("td")
    matches_dict["pos"]  = re.sub('\s+',' ',common_td_list[0].text)
    matches_dict["team"]  = re.sub('\s+',' ',common_td_list[1].findAll("span")[1].text)
    matches_dict["match"] = re.sub('\s+',' ',common_td_list[2].text)
    matches_dict["points"]  = re.sub('\s+',' ',common_td_list[3].text)
    matches_dict["rating"]  = re.sub('\s+',' ',common_td_list[4].text)
    matches_list.append(matches_dict)
   
    
result_dict["Ranking"] = matches_list

json_output=json.dumps(result_dict)

print(json_output.replace(" ","").replace("(GMT)",""))
f = open("mens_team-rankings_t20", "w")
f.write(str(json_output))
f.close()


##########################_ICC_____ODI-TEAM_____RANKING_##########################

url_1 = "https://www.icc-cricket.com/rankings/mens/team-rankings/odi"

r_1 = requests.get(url_1)

soup_1 = BeautifulSoup(r_1.text, "lxml")

header_dict_1= {}
result_dict_1= {}
header_list_1= []
matches_dict_1= {}
matches_list_1= []
names_4 = soup_1.find("div", class_ = "rankings-block__title-container").text
names1_5 = soup_1.find("div", class_ = "rankings-table__last-updated").text

result_dict_1["title"] =  re.sub('\s+',' ',names_4)
result_dict_1["last_update"] = re.sub('\s+',' ',names1_5 )

# print(names, names1.replace("(GMT)",""))


names2_6 = soup_1.find("tbody")
comman_th_list_1 = names2_6.find("tr",class_ = "rankings-block__banner").findAll("td")

matches_dict_1["pos"]  = re.sub('\s+',' ',comman_th_list_1[0].text)
matches_dict_1["team"] =  re.sub('\s+',' ',comman_th_list_1[1].findAll("span")[1].text)
matches_dict_1["match"] = re.sub('\s+',' ',comman_th_list_1[2].text)
matches_dict_1["points"]  = re.sub('\s+',' ',comman_th_list_1[3].text)
matches_dict_1["rating"] =  re.sub('\s+',' ',comman_th_list_1[4].text)

matches_list_1.append(matches_dict_1)
names3_7 = names2_6.findAll("tr", class_ = "table-body")


for i in names3_7:
    matches_dict_1 = {}
    common_td_list_1 = i.findAll("td")
    matches_dict_1["pos"]  = re.sub('\s+',' ',common_td_list_1[0].text)
    matches_dict_1["team"]  = re.sub('\s+',' ',common_td_list_1[1].findAll("span")[1].text)
    matches_dict_1["match"] = re.sub('\s+',' ',common_td_list_1[2].text)
    matches_dict_1["points"]  = re.sub('\s+',' ',common_td_list_1[3].text)
    matches_dict_1["rating"]  = re.sub('\s+',' ',common_td_list_1[4].text)
    matches_list_1.append(matches_dict_1)
   
    
result_dict_1["Ranking"] = matches_list_1

json_output_1=json.dumps(result_dict_1)

print(json_output_1.replace(" ","").replace("(GMT)",""))
f = open("mens_team-rankings_odi", "w")
f.write(str(json_output_1))
f.close()


##########################_ICC_____TEST-TEAM_____RANKING_##########################


url_2 = "https://www.icc-cricket.com/rankings/mens/team-rankings/test"

r_2 = requests.get(url_2)

soup_2 = BeautifulSoup(r_2.text, "lxml")

header_dict_2 = {}
result_dict_2 = {}
header_list_2 = []
matches_dict_2 = {}
matches_list_2 = []
names_8 = soup_2.find("div", class_ = "rankings-block__title-container").text
names1_9 = soup_2.find("div", class_ = "rankings-table__last-updated").text

result_dict_2["title"] =  re.sub('\s+',' ',names_8)
result_dict_2["last_update"] = re.sub('\s+',' ',names1_9 )

# print(names, names1.replace("(GMT)",""))


names2_10 = soup_2.find("tbody")
comman_th_list_2 = names2_10.find("tr",class_ = "rankings-block__banner").findAll("td")

matches_dict_2["pos"]  = re.sub('\s+',' ',comman_th_list_2[0].text)
matches_dict_2["team"] =  re.sub('\s+',' ',comman_th_list_2[1].findAll("span")[1].text)
matches_dict_2["match"] = re.sub('\s+',' ',comman_th_list_2[2].text)
matches_dict_2["points"]  = re.sub('\s+',' ',comman_th_list_2[3].text)
matches_dict_2["rating"] =  re.sub('\s+',' ',comman_th_list_2[4].text)

matches_list_2.append(matches_dict_2)
names3_11 = names2_10.findAll("tr", class_ = "table-body")


for i in names3_11:
    matches_dict_2 = {}
    common_td_list_2 = i.findAll("td")
    matches_dict_2["pos"]  = re.sub('\s+',' ',common_td_list_2[0].text)
    matches_dict_2["team"]  = re.sub('\s+',' ',common_td_list_2[1].findAll("span")[1].text)
    matches_dict_2["match"] = re.sub('\s+',' ',common_td_list_2[2].text)
    matches_dict_2["points"]  = re.sub('\s+',' ',common_td_list_2[3].text)
    matches_dict_2["rating"]  = re.sub('\s+',' ',common_td_list_2[4].text)
    matches_list_2.append(matches_dict_2)
   
    
result_dict_2["Ranking"] = matches_list_2
json_output_2=json.dumps(result_dict_2)

print(json_output_2.replace(" ","").replace("(GMT)",""))
f = open("mens_team-rankings_test", "w")
f.write(str(json_output_2))
f.close()


##########################_ICC_____T20-MEN_____RANKING_##########################


url_3 = "https://www.icc-cricket.com/rankings/mens/player-rankings/t20i/batting"



r_3 = requests.get(url_3)
soup_3 = BeautifulSoup(r_3.text, "lxml")

header_dict_3 = {}
result_dict_3 = {}
header_list_3= []
matches_dict_3= {}
matches_list_3 = []

names_12 = soup_3.find("div", class_ = "rankings-block__title-container").text
names1_13 = soup_3.find("div", class_ = "rankings-block__meta-container").text
result_dict_3["title"] = re.sub('\s+',' ',names_12)
result_dict_3["last_update"] = re.sub('\s+',' ',names1_13)



comman_th_list_3= soup_3.find("table", class_="table rankings-table").find("tr",class_="rankings-block__banner").findAll("td")
matches_dict_3["pos"]  = re.sub('\s+',' ',comman_th_list_3[0].div.span.text)
matches_dict_3["player"] =  re.sub('\s+',' ',comman_th_list_3[1].a.text)
matches_dict_3["team"] = re.sub('\s+',' ',comman_th_list_3[2].text)
matches_dict_3["rating"]  = re.sub('\s+',' ',comman_th_list_3[3].text)
matches_dict_3["career_best_rating"] =  re.sub('\s+',' ',comman_th_list_3[4].text)

matches_list_3.append(matches_dict_3)
names2_14 = soup_3.find("table", class_="table rankings-table").findAll("tr", class_="table-body")
for i in names2_14:
    matches_dict_3 = {}
    common_td_list_3 = i.findAll("td")
    matches_dict_3["pos"]  = re.sub('\s+',' ',common_td_list_3[0].div.span.text)
    matches_dict_3["player"]  = re.sub('\s+',' ',common_td_list_3[1].a.text)
    matches_dict_3["team"] = re.sub('\s+',' ',common_td_list_3[2].text)
    matches_dict_3["rating"]  = re.sub('\s+',' ',common_td_list_3[3].text)
    matches_dict_3["career_best_rating"]  = re.sub('\s+',' ',common_td_list_3[4].text)
    matches_list_3.append(matches_dict_3)


result_dict_3["ranking"] = matches_list_3
json_output_3=json.dumps(result_dict_3)

print(json_output_3.replace(" ","").replace("(GMT)",""))
f = open("mens_player-rankings_t20_batting", "w")
f.write(str(json_output_3))
f.close()


##########################_ICC_____T20-MEN-BOWL_____RANKING_##########################


url_4 = "https://www.icc-cricket.com/rankings/mens/player-rankings/t20i/bowling"



r_4 = requests.get(url_4)
soup_4 = BeautifulSoup(r_4.text, "lxml")

header_dict_4 = {}
result_dict_4 = {}
header_list_4= []
matches_dict_4 = {}
matches_list_4 = []

names_15 = soup_4.find("div", class_ = "rankings-block__title-container").text
names1_16 = soup_4.find("div", class_ = "rankings-block__meta-container").text
result_dict_4["title"] = re.sub('\s+',' ',names_15)
result_dict_4["last_update"] = re.sub('\s+',' ',names1_16)




comman_th_list_4 = soup_4.find("table", class_="table rankings-table").find("tr",class_="rankings-block__banner").findAll("td")
matches_dict_4["pos"]  = re.sub('\s+',' ',comman_th_list_4[0].div.span.text)
matches_dict_4["player"] =  re.sub('\s+',' ',comman_th_list_4[1].a.text)
matches_dict_4["team"] = re.sub('\s+',' ',comman_th_list_4[2].text)
matches_dict_4["rating"]  = re.sub('\s+',' ',comman_th_list_4[3].text)
matches_dict_4["career_best_rating"] =  re.sub('\s+',' ',comman_th_list_4[4].text)

matches_list_4.append(matches_dict_4)


names2_17 = soup_4.find("table", class_="table rankings-table").findAll("tr", class_="table-body")
for i in names2_17:
    matches_dict = {}
    common_td_list_4 = i.findAll("td")
    matches_dict_4["pos"]  = re.sub('\s+',' ',common_td_list_4[0].div.span.text)
    matches_dict_4["player"]  = re.sub('\s+',' ',common_td_list_4[1].a.text)
    matches_dict_4["team"] = re.sub('\s+',' ',common_td_list_4[2].text)
    matches_dict_4["rating"]  = re.sub('\s+',' ',common_td_list_4[3].text)
    matches_dict_4["career_best_rating"]  = re.sub('\s+',' ',common_td_list_4[4].text)
    matches_list_4.append(matches_dict_4)

print(matches_list_4)

result_dict_4["ranking"] = matches_list_4
json_output_4=json.dumps(result_dict_4)

print(json_output_4)
f = open("mens_player-rankings_bowling", "w")
f.write(str(json_output_4))
f.close()


##########################_ICC_____T20-MEN-ALLROUNDER_____RANKING_##########################



url_5 = "https://www.icc-cricket.com/rankings/mens/player-rankings/t20i/all-rounder"



r_5 = requests.get(url_5)
soup_5 = BeautifulSoup(r_5.text, "lxml")

header_dict_5 = {}
result_dict_5 = {}
header_list_5 = []
matches_dict_5 = {}
matches_list_5 = []

names_18 = soup_5.find("div", class_ = "rankings-block__title-container").text
names1_19= soup_5.find("div", class_ = "rankings-block__meta-container").text
result_dict_5["title"] = re.sub('\s+',' ',names_18)
result_dict_5["last_update"] = re.sub('\s+',' ',names1_19)





comman_th_list_5 = soup_5.find("table", class_="table rankings-table").find("tr",class_="rankings-block__banner").findAll("td")
matches_dict_5["pos"]  = re.sub('\s+',' ',comman_th_list_5[0].div.span.text)
matches_dict_5["player"] =  re.sub('\s+',' ',comman_th_list_5[1].a.text)
matches_dict_5["team"] = re.sub('\s+',' ',comman_th_list_5[2].text)
matches_dict_5["rating"]  = re.sub('\s+',' ',comman_th_list_5[3].text)
matches_dict_5["career_best_rating"] =  re.sub('\s+',' ',comman_th_list_5[4].text)

matches_list_5.append(matches_dict_5)


names2_20 = soup_5.find("table", class_="table rankings-table").findAll("tr", class_="table-body")
for i in names2_20:
    matches_dict_5 = {}
    common_td_list_5 = i.findAll("td")
    matches_dict_5["pos"]  = re.sub('\s+',' ',common_td_list_5[0].div.span.text)
    matches_dict_5["player"]  = re.sub('\s+',' ',common_td_list_5[1].a.text)
    matches_dict_5["team"] = re.sub('\s+',' ',common_td_list_5[2].text)
    matches_dict_5["rating"]  = re.sub('\s+',' ',common_td_list_5[3].text)
    matches_dict_5["career_best_rating"]  = re.sub('\s+',' ',common_td_list_5[4].text)
    matches_list_5.append(matches_dict_5)



result_dict_5["ranking"] = matches_list_5
json_output_5=json.dumps(result_dict_5)

print(json_output_5)
f = open("mens_player-rankings_t20_allrounder", "w")
f.write(str(json_output_5))
f.close()


##########################_ICC_____ODI-MEN_____RANKING_##########################


url_6 = "https://www.icc-cricket.com/rankings/mens/player-rankings/odi/batting"

r_6 = requests.get(url_6)
soup_6 = BeautifulSoup(r_6.text, "lxml")


header_dict_6 = {}
result_dict_6 = {}
header_list_6 = []
matches_dict_6 = {}
matches_list_6 = []


names_21 = soup_6.find("div", class_ = "rankings-block__title-container").text
names1_22 = soup_6.find("div", class_ = "rankings-block__meta-container").text
result_dict_6["title"] = re.sub('\s+',' ',names_21)
result_dict_6["last_update"] = re.sub('\s+',' ',names1_22)



comman_th_list_6 = soup_6.find("table", class_="table rankings-table").find("tr",class_="rankings-block__banner").findAll("td")
matches_dict_6["pos"]  = re.sub('\s+',' ',comman_th_list_6[0].div.span.text)
matches_dict_6["player"] =  re.sub('\s+',' ',comman_th_list_6[1].a.text)
matches_dict_6["team"] = re.sub('\s+',' ',comman_th_list_6[2].text)
matches_dict_6["rating"]  = re.sub('\s+',' ',comman_th_list_6[3].text)
matches_dict_6["career_best_rating"] =  re.sub('\s+',' ',comman_th_list_6[4].text)

matches_list_6.append(matches_dict_6)


names2_23 = soup_6.find("table", class_="table rankings-table").findAll("tr", class_="table-body")
for i in names2_23:
    matches_dict_6 = {}
    common_td_list_6 = i.findAll("td")
    matches_dict_6["pos"]  = re.sub('\s+',' ',common_td_list_6[0].div.span.text)
    matches_dict_6["player"]  = re.sub('\s+',' ',common_td_list_6[1].a.text)
    matches_dict_6["team"] = re.sub('\s+',' ',common_td_list_6[2].text)
    matches_dict_6["rating"]  = re.sub('\s+',' ',common_td_list_6[3].text)
    matches_dict_6["career_best_rating"]  = re.sub('\s+',' ',common_td_list[4].text)
    matches_list_6.append(matches_dict_6)

print(matches_list_6)

result_dict_6["ranking"] = matches_list_6
json_output_6=json.dumps(result_dict_6)

# print(json_output.replace(" ","").replace("(GMT)",""))
f = open("mens_player-rankings_odi_batting", "w")
f.write(str(json_output_6))
f.close()


##########################_ICC_____ODI-MEN-BOWL_____RANKING_##########################



url_7 = "https://www.icc-cricket.com/rankings/mens/player-rankings/odi/bowling"

r_7 = requests.get(url_7)
soup_7 = BeautifulSoup(r_7.text, "lxml")


header_dict_7 = {}
result_dict_7 = {}
header_list_7 = []
matches_dict_7= {}
matches_list_7 = []


names_24 = soup_7.find("div", class_ = "rankings-block__title-container").text
names1_25 = soup_7.find("div", class_ = "rankings-block__meta-container").text
result_dict_7["title"] = re.sub('\s+',' ',names_24)
result_dict_7["last_update"] = re.sub('\s+',' ',names1_25 )



comman_th_list_7 = soup_7.find("table", class_="table rankings-table").find("tr",class_="rankings-block__banner").findAll("td")
matches_dict_7["pos"]  = re.sub('\s+',' ',comman_th_list_7[0].div.span.text)
matches_dict_7["player"] =  re.sub('\s+',' ',comman_th_list_7[1].a.text)
matches_dict_7["team"] = re.sub('\s+',' ',comman_th_list_7[2].text)
matches_dict_7["rating"]  = re.sub('\s+',' ',comman_th_list_7[3].text)
matches_dict_7["career_best_rating"] =  re.sub('\s+',' ',comman_th_list_7[4].text)

matches_list_7.append(matches_dict_7)


names2_26 = soup_7.find("table", class_="table rankings-table").findAll("tr", class_="table-body")
for i in names2_26:
    matches_dict_7 = {}
    common_td_list_7 = i.findAll("td")
    matches_dict_7["pos"]  = re.sub('\s+',' ',common_td_list_7[0].div.span.text)
    matches_dict_7["player"]  = re.sub('\s+',' ',common_td_list_7[1].a.text)
    matches_dict_7["team"] = re.sub('\s+',' ',common_td_list_7[2].text)
    matches_dict_7["rating"]  = re.sub('\s+',' ',common_td_list_7[3].text)
    matches_dict_7["career_best_rating"]  = re.sub('\s+',' ',common_td_list_7[4].text)
    matches_list_7.append(matches_dict_7)

print(matches_list_7)

result_dict_7["ranking"] = matches_list_7
json_output_7=json.dumps(result_dict_7)

# print(json_output.replace(" ","").replace("(GMT)",""))
f = open("mens_player-rankings_odi_bowling", "w")
f.write(str(json_output_7))
f.close()


##########################_ICC_____ODI-MEN-ALLROUNDER_____RANKING_##########################


url_8 = "https://www.icc-cricket.com/rankings/mens/player-rankings/odi/all-rounder"



r_8 = requests.get(url_8)
soup_8 = BeautifulSoup(r_8.text, "lxml")

header_dict_8 = {}
result_dict_8 = {}
header_list_8 = []
matches_dict_8 = {}
matches_list_8 = []

names_27 = soup_8.find("div", class_ = "rankings-block__title-container").text
names1_28 = soup_8.find("div", class_ = "rankings-block__meta-container").text
result_dict["title"] = re.sub('\s+',' ',names_27)
result_dict["last_update"] = re.sub('\s+',' ',names1_28)





comman_th_list_8 = soup_8.find("table", class_="table rankings-table").find("tr",class_="rankings-block__banner").findAll("td")
matches_dict_8["pos"]  = re.sub('\s+',' ',comman_th_list_8[0].div.span.text)
matches_dict_8["player"] =  re.sub('\s+',' ',comman_th_list_8[1].a.text)
matches_dict_8["team"] = re.sub('\s+',' ',comman_th_list_8[2].text)
matches_dict_8["rating"]  = re.sub('\s+',' ',comman_th_list_8[3].text)
matches_dict_8["career_best_rating"] =  re.sub('\s+',' ',comman_th_list_8[4].text)

matches_list_8.append(matches_dict_8)


names2_29 = soup_8.find("table", class_="table rankings-table").findAll("tr", class_="table-body")
for i in names2_29:
    matches_dict_8 = {}
    common_td_list_8 = i.findAll("td")
    matches_dict_8["pos"]  = re.sub('\s+',' ',common_td_list_8[0].div.span.text)
    matches_dict_8["player"]  = re.sub('\s+',' ',common_td_list_8[1].a.text)
    matches_dict_8["team"] = re.sub('\s+',' ',common_td_list_8[2].text)
    matches_dict_8["rating"]  = re.sub('\s+',' ',common_td_list_8[3].text)
    matches_dict_8["career_best_rating"]  = re.sub('\s+',' ',common_td_list_8[4].text)
    matches_list_8.append(matches_dict_8)

print(matches_list_8)

result_dict_8["ranking"] = matches_list_8
json_output_8=json.dumps(result_dict_8)

print(json_output_8)
f = open("mens_player-rankings_odi_allrounder", "w")
f.write(str(json_output_8))
f.close()

##########################_ICC_____TEST -MEN _##########################



url_9 = "https://www.icc-cricket.com/rankings/mens/player-rankings/test/batting"



r_9 = requests.get(url_9)
soup_9 = BeautifulSoup(r_9.text, "lxml")

header_dict_9 = {}
result_dict_9 = {}
header_list_9 = []
matches_dict_9 = {}
matches_list_9 = []

names_30 = soup.find("div", class_ = "rankings-block__title-container").text
names1_31 = soup.find("div", class_ = "rankings-block__meta-container").text
result_dict["title"] = re.sub('\s+',' ',names_30)
result_dict["last_update"] = re.sub('\s+',' ',names1_31)





comman_th_list_9 = soup_9.find("table", class_="table rankings-table").find("tr",class_="rankings-block__banner").findAll("td")
matches_dict_9["pos"]  = re.sub('\s+',' ',comman_th_list_9[0].div.span.text)
matches_dict_9["player"] =  re.sub('\s+',' ',comman_th_list_9[1].a.text)
matches_dict_9["team"] = re.sub('\s+',' ',comman_th_list_9[2].text)
matches_dict_9["rating"]  = re.sub('\s+',' ',comman_th_list_9[3].text)
matches_dict_9["career_best_rating"] =  re.sub('\s+',' ',comman_th_list_9[4].text)

matches_list_9.append(matches_dict_9)


names2_32 = soup_9.find("table", class_="table rankings-table").findAll("tr", class_="table-body")
for i in names2_32:
    matches_dict_9 = {}
    common_td_list_9 = i.findAll("td")
    matches_dict_9["pos"]  = re.sub('\s+',' ',common_td_list_9[0].div.span.text)
    matches_dict_9["player"]  = re.sub('\s+',' ',common_td_list_9[1].a.text)
    matches_dict_9["team"] = re.sub('\s+',' ',common_td_list_9[2].text)
    matches_dict_9["rating"]  = re.sub('\s+',' ',common_td_list_9[3].text)
    matches_dict_9["career_best_rating"]  = re.sub('\s+',' ',common_td_list_9[4].text)
    matches_list_9.append(matches_dict_9)

print(matches_list_9)

result_dict_9["ranking"] = matches_list_9
json_output_9=json.dumps(result_dict_9)

print(json_output_9)
f = open("mens_player-rankings_test_batting", "w")
f.write(str(json_output_9))
f.close()

##########################_ICC_TEST_BOWL_##########################



url_10= "https://www.icc-cricket.com/rankings/mens/player-rankings/test/bowling"



r_10= requests.get(url_10)
soup_10= BeautifulSoup(r_10.text, "lxml")

header_dict_10 = {}
result_dict_10 = {}
header_list_10 = []
matches_dict_10 = {}
matches_list_10 = []

names_33 = soup_10.find("div", class_ = "rankings-block__title-container").text
names1_34 = soup_10.find("div", class_ = "rankings-block__meta-container").text
result_dict_10["title"] = re.sub('\s+',' ',names_33)
result_dict_10["last_update"] = re.sub('\s+',' ',names1_34)





comman_th_list_10 = soup_10.find("table", class_="table rankings-table").find("tr",class_="rankings-block__banner").findAll("td")
matches_dict_10["pos"]  = re.sub('\s+',' ',comman_th_list_10[0].div.span.text)
matches_dict_10["player"] =  re.sub('\s+',' ',comman_th_list_10[1].a.text)
matches_dict_10["team"] = re.sub('\s+',' ',comman_th_list_10[2].text)
matches_dict_10["rating"]  = re.sub('\s+',' ',comman_th_list_10[3].text)
matches_dict_10["career_best_rating"] =  re.sub('\s+',' ',comman_th_list_10[4].text)

matches_list_10.append(matches_dict_10)


names2_35= soup_10.find("table", class_="table rankings-table").findAll("tr", class_="table-body")
for i in names2_35:
    matches_dict_10= {}
    common_td_list_10 = i.findAll("td")
    matches_dict_10["pos"]  = re.sub('\s+',' ',common_td_list_10[0].div.span.text)
    matches_dict_10["player"]  = re.sub('\s+',' ',common_td_list_10[1].a.text)
    matches_dict_10["team"] = re.sub('\s+',' ',common_td_list_10[2].text)
    matches_dict_10["rating"]  = re.sub('\s+',' ',common_td_list_10[3].text)
    matches_dict_10["career_best_rating"]  = re.sub('\s+',' ',common_td_list_10[4].text)
    matches_list_10.append(matches_dict_10)

print(matches_list_10)

result_dict_10["ranking"] = matches_list_10
json_output_10=json.dumps(result_dict_10)

print(json_output_10)
f = open("mens_player-rankings_test_bowling", "w")
f.write(str(json_output_10))
f.close()


##########################_ICC_TEST_ALLROUNDER_##########################


url_11 = "https://www.icc-cricket.com/rankings/mens/player-rankings/test/all-rounder"


r_11 = requests.get(url_11)
soup_11 = BeautifulSoup(r_11.text, "lxml")

header_dict_11 = {}
result_dict_11 = {}
header_list_11 = []
matches_dict_11 = {}
matches_list_11 = []

names_36 = soup.find("div", class_ = "rankings-block__title-container").text
names1_37 = soup.find("div", class_ = "rankings-block__meta-container").text
result_dict_11["title"] = re.sub('\s+',' ',names_36)
result_dict_11["last_update"] = re.sub('\s+',' ',names1_37)





comman_th_list_11 = soup_11.find("table", class_="table rankings-table").find("tr",class_="rankings-block__banner").findAll("td")
matches_dict_11["pos"]  = re.sub('\s+',' ',comman_th_list_11[0].div.span.text)
matches_dict_11["player"] =  re.sub('\s+',' ',comman_th_list_11[1].a.text)
matches_dict_11["team"] = re.sub('\s+',' ',comman_th_list_11[2].text)
matches_dict_11["rating"]  = re.sub('\s+',' ',comman_th_list_11[3].text)
matches_dict_11["career_best_rating"] =  re.sub('\s+',' ',comman_th_list_11[4].text)

matches_list_11.append(matches_dict_11)


names2_38 = soup_11.find("table", class_="table rankings-table").findAll("tr", class_="table-body")
for i in names2_38:
    matches_dict_11 = {}
    common_td_list_11 = i.findAll("td")
    matches_dict_11["pos"]  = re.sub('\s+',' ',common_td_list_11[0].div.span.text)
    matches_dict_11["player"]  = re.sub('\s+',' ',common_td_list_11[1].a.text)
    matches_dict_11["team"] = re.sub('\s+',' ',common_td_list_11[2].text)
    matches_dict_11["rating"]  = re.sub('\s+',' ',common_td_list_11[3].text)
    matches_dict_11["career_best_rating"]  = re.sub('\s+',' ',common_td_list_11[4].text)
    matches_list_11.append(matches_dict_11)

#print(matches_list_11)

result_dict_11["ranking"] = matches_list_11
json_output_11=json.dumps(result_dict_11)

print(json_output_11)
f = open("mens_player-rankings_test_all-rounder", "w")
f.write(str(json_output_11))
f.close()
























