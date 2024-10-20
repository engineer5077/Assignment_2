# Assignment_2

% Author Name: [Albert Malizia]
% Email: [malizi49@students.rowan.edu]
% Course: MATLAB Programming - Fall 2024
% Assignment: Assignment 2
% Task: [Assignment 2]
% Date: [October 18th 2024]

% Population Growth Analysis

% a) Create the population vector
population = [5000, 5200, 5350, 5600, 5800];

% b) Calculate the growth rate
growth_rate = (population(2:end) - population(1:end-1)) ./ population(1:end-1);

% c) Create the pop_data matrix
pop_data = [population; [0 growth_rate]];

% d) Print the formatted table
fprintf('Year\tPopulation\tGrowth Rate\n');
for i = 1:length(population)
    fprintf('%d \t%d \t \t%.2f%% \n', i, population(i), pop_data(2, i));
end

% -----------------------------------

% Weather Data Analysis

% a) Create a file named 'weather_data.txt' with the following structure:
% I tried to import the weather.txt into github but could not figure it
% out, so I typed the data into matlab itself
fileID = fopen('weather_data.txt');
fprintf(fileID, 'Date, Temperature, Humidity, Precipitation \n');
fprintf(fileID, '2024-09-01, 25.5, 60, 0 \n');
fprintf(fileID, '2024-09-02, 26.0,65, 5 \n');
fprintf(fileID, '2024-09-03, 24.5, 70, 10 \n');
fprintf(fileID, '2024-09-04, 23.0, 75, 15 \n');
fprintf(fileID, '2024-09-05, 22.5, 80, 20 \n');
fclose(fileID);

% b) Write a MATLAB script that:

fileID = fopen('weather_data.txt', 'r');

% Read data from file
data = readcell('weather_data.txt', 'Delimiter', ',');

% Extract numerical data into seperate vectors
temperature = cell2mat(data(2:end, 2));
humidity = cell2mat(data(2:end, 3));
precipitation = cell2mat(data(2:end, 4));

% Calculates the Statistics
avgerage_temperature = mean(temperature);
avgerage_humidity = mean(humidity);
total_precipitation = sum(precipitation);

% Save the Statistics to a new file called weather_summary.txt
summaryID = fopen('weather_summary.txt');
fprintf(summaryID, 'Average Temperature: %.2f\n', avgerage_temperature);
fprintf(summaryID, 'Average Humidity: %.2f\n', avgerage_humidity);
fprintf(summaryID, 'Total Precipitation: %.2f\n', total_precipitation);
fclose(summaryID);

% -------------------------------

% Solar System Visualization

% a) Create two vectors (Relative to Earth = 1)
% Average distance from the Sun
planet_distances = [0.39, 0.72, 1.00, 1.52, 5.20, 9.54, 19.22, 30.06]; % Mercury, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune
% Relative Size of planets (Relative to Earth = 1)
planet_sizes = [0.3, 0.9, 1.0, 0.5, 11.0, 9.0, 4.0, 3.8]; % Mercury, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune

% b) Create a figure with two subplots
plaet_names = {'Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune'};
