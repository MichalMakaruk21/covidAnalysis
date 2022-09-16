__---------------PL---------------__

__Celem projektu jest wyliczenie i predykcja dziennego współczynnika śmiertelności na COVID-19 w wybranych krajach świata.__

Z powodu niewystarczających zasobów na koncie studenckim na Azure Portal nie mogłem utworzyć klastra na Azure DataBricks. Doprowadziło to przymusu operowania na okrojonych danych tylko do kilku krajów europejskich. W wypadku większej mocy CPU, skrypt umożliwia taką możliwość, wystarczy odkomentować jedną oraz zakomentować dwie linijki. 

__Źródła danych:__

WHO - Ilość zachorowań i śmierci z rozdzieleniem na kraje, kod ISO2 , datę dzienną.

OWID - publiczne repozytorium przetrzymujące dzienne dane dot. covid. WHO nie od jakiegoś czasu nie aktualizuje tych danych do pobrania. Dlatego OWID był najlepszą alternatywą. Rozdzielenie na kraje, kod ISO3 , datę dzienną.
link: https://github.com/owid/covid-19-data/tree/master/public/data

Wikipedia - Tabela słownikowa zawierająca kraj, kod ISO2 i kod ISO3.

__Pre-Precessing__

MissForrest() - Transformator zbudowany na bazie RandomForrest z biblioteki "sklearn", jednak dostępny w bibliotece "missingpy" . Uzupełnia wartości NaN w danych za pomocą ML.

StnadardScaller() - Standaryzacja cech poprzez przeskalowanie do wariancji jednostkowej.

Pipeline() - Klasa zawierająca w sobie zdefiniowany transformator("MissForrest()") oraz skaler("StandardScaller()"). Operacje pre-procesingu wykonuje się w jednym wywołaniu za pomocą metody "fit_transform()".
link: https://gbhat.com/machine-learning/scikit_learn_ml_regression_pipeline.html

__ML model__

RandomForestRegressor() - Eestymator zbudowany na postawie klasyfikatora RandomForrest. 

__Co można poprawić?__

Obliczenie wskaźnika śmiertelności jest wykonywane między pre-procesingiem a modelowaniem. Lepszą opcją byłoby stworzenie klasy/funkcji która zostałaby wywołana jako ostatnia w pipeline, którego output mógłby być od razu wczytany do modelu. Doprowadziło by to do większej obiektowości projektu i poprawiło jakość kodu. 

__--------------ENG---------------__

__The purpose of the project is to calculate and predict the daily mortality rate on COVID-19 in selected countries around the world.__

Due to inadequate resources in the student account on Azure Portal, I could not create a cluster on Azure DataBricks. This led to a forced operation on truncated data to only a few European countries. In case of more CPU power, the script allows this possibility, just uncomment one and comment out two lines. 

__Data sources:_

WHO - Number of illnesses and deaths separated by country, ISO2 code, daily date.

OWID - public repository holding daily covid data. WHO has not updated this downloadable data for some time. Therefore, OWID was the best alternative. Separate by country, ISO3 code , daily date.
Link: https://github.com/owid/covid-19-data/tree/master/public/data

Wikipedia - Dictionary table including country, ISO2 code and ISO3 code.

__Pre-Precessing__

MissForrest() - Transformer built on RandomForrest from the "sklearn" library, but available in the "missingpy" library . Complements NaN values in the data using ML.

StnadardScaller() - Standardizes features by scaling to unit variance.

Pipeline() - A class containing a defined transformer("MissForrest()") and scaler("StandardScaller()"). Pre-processing operations are performed in a single call using the "fit_transform()" method.
link: https://gbhat.com/machine-learning/scikit_learn_ml_regression_pipeline.html

__ML model__

RandomForestRegressor() - Eestimator built on the basis of RandomForrest classifier. 

__What can be improved?__

Calculating the mortality rate is done between pre-processing and modeling. A better option would be to create a class/function that would be called as last in the pipeline, whose output could be loaded into the model right away. This would lead to a more object-oriented design and improve code quality. 
