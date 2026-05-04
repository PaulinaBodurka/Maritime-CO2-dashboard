# Maritime-CO2-dashboard
ESG dashboard for maritime CO₂ emissions analysis | DNV MRV data | Power BI
I built an ESG dashboard for maritime CO₂ fleet emissions, based on DNV MRV data — from raw files all the way to an interactive four-page report.
<img width="1116" height="624" alt="3" src="https://github.com/user-attachments/assets/abba4ade-9ef0-45e8-b135-17861b5d6430" />
<img width="1106" height="609" alt="2" src="https://github.com/user-attachments/assets/6f7c2078-214a-4304-95b1-d0411a23c669" />
<img width="1111" height="619" alt="1" src="https://github.com/user-attachments/assets/277e83a5-77dd-4a67-9666-cbc564e5970f" />
<img width="954" height="537" alt="0" src="https://github.com/user-attachments/assets/e2674b04-f827-433e-a5ae-b54bdf5d3c41" />

What was the hardest part? Not the visualisation. The data. 😅

The same port would show up under completely different names — typos, different languages, abbreviations, local variants. To correctly map emissions to locations, I had to use fuzzy matching to standardize port names. Sounds simple, but in practice it takes a lot of iteration and validation.

Other building blocks:
🔹 ETL pipeline to process raw MRV data
🔹 Star schema model with dimension tables — vessel, port, ship type, verifier, year
🔹 Port-to-country mapping for geographic analysis

One thing worth understanding when reading this kind of data:

📍 Emissions on the map are shown by the vessel's port of registry — not by where the emissions actually happen. Liberia and the Bahamas look like major emitters because many ships register there for regulatory reasons. That's the flag of convenience effect — the pollution isn't coming from those countries.

The dashboard covers the gap to IMO 2030 targets, technical efficiency distribution (EEXI/EEDI), and who verifies the fleet.

And it's built to grow — new data years, additional metrics, or new analytical views can be plugged in without starting over. If you have ideas for what's missing, I'm all ears.

I'd really appreciate any feedback — from data folks, maritime professionals, or anyone working in ESG. What do you see that I'm missing?

#ESG #MaritimeEmissions #DataAnalytics #Decarbonization #PowerBI #ETL #Sustainability #IMO2030 #EUETS


[🔗 View interactive dashboard](https://app.powerbi.com/view?r=eyJrIjoiMjFmODRiYjctMjE5OC00ZGVjLTgxMmMtMmExMzUzYzk2YmQyIiwidCI6IjNkZmU5YWI2LTgxYmYtNDkxYy1iNjcwLTAxYzgyNGEwOWUxOSJ9)
