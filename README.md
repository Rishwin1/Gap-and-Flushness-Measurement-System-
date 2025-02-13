# Gap-and-Flushness-Measurement-System-
ˇ#include <iostream>
#include <vector>
#include <cmath>
#include <algorithm>

struct Point {
    double x, y, z;
};

double calculateDistance(const Point& p1, const Point& p2) {
    return std::sqrt(std::pow(p1.x - p2.x, 2) + std::pow(p1.y - p2.y, 2) + std::pow(p1.z - p2.z, 2));
}

double calculateAverageGap(const std::vector<Point>& surface1, const std::vector<Point>& surface2) {
    double totalGap = 0.0;
    for (size_t i = 0; i < surface1.size(); ++i) {
        totalGap += calculateDistance(surface1[i], surface2[i]);
    }
    return totalGap / surface1.size();
}

double calculateFlushness(const std::vector<Point>& surface1, const std::vector<Point>& surface2) {
    double maxFlushness = 0.0;
    for (size_t i = 0; i < surface1.size(); ++i) {
        double distance = calculateDistance(surface1[i], surface2[i]);
        if (distance > maxFlushness) {
            maxFlushness = distance;
        }
    }
    return maxFlushness;
}

int main() {
    // Example surfaces represented by a set of points
    std::vector<Point> surface1 = {
        {0.0, 0.0, 0.0},
        {1.0, 0.0, 0.0},
        {0.0, 1.0, 0.0},
        {1.0, 1.0, 0.0}
    };

    std::vector<Point> surface2 = {
        {0.0, 0.0, 0.1},
        {1.0, 0.0, 0.1},
        {0.0, 1.0, 0.1},
        {1.0, 1.0, 0.1}
    };

    // Calculate the average gap between the two surfaces
    double averageGap = calculateAverageGap(surface1, surface2);
    std::cout << "Average Gap: " << averageGap << " units" << std::endl;

    // Calculate the flushness between the two surfaces
    double flushness = calculateFlushness(surface1, surface2);
    std::cout << "Flushness: " << flushness << " units" << std::endl;

    return 0;
}
