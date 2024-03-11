#include <stdio.h>
#include <stdlib.h>

float mm_to_cm(float mm) { return mm / 10; }
float cm_to_m(float cm) { return cm / 100; }
float m_to_km(float m) { return m / 1000; }
float m_to_wa(float m) { return m / 2; }
float km_to_mile(float km) { return km * 0.621371; }

int main() {
  FILE *fp;
  int opt;

  fp = fopen("result.txt", "a");

  while (1) {
    system("clear");
    printf("Option List:\n");
    printf("\"1\" Millimeter to Centimeter\n");
    printf("\"2\" Centimeter to Meter\n");
    printf("\"3\" Meter to Kilometer\n");
    printf("\"4\" Meter to Wa\n");
    printf("\"5\" Kilometer to Mile\n");
    printf("\"0\" Exit Program\n");
    printf("Choose your option: ");
    scanf("%d", &opt);

    while (opt < 0 || opt > 5) {
      printf("Invalid option. Please choose again: ");
      scanf("%d", &opt);
    }

    if (opt == 0) {
      printf("Exiting program...\n");
      break;
    } else if (opt == 1) {
      float mm;
      printf("Enter the value in millimeter: ");
      scanf("%f", &mm);
      printf("The value in centimeter is: %.2f\n", mm_to_cm(mm));
      fprintf(fp, "%.2f mm = %.2f cm\n", mm, mm_to_cm(mm));
    } else if (opt == 2) {
      float cm;
      printf("Enter the value in centimeter: ");
      scanf("%f", &cm);
      printf("The value in meter is: %.2f\n", cm_to_m(cm));
      fprintf(fp, "%.2f cm = %.2f m\n", cm, cm_to_m(cm));
    } else if (opt == 3) {
      float m;
      printf("Enter the value in meter: ");
      scanf("%f", &m);
      printf("The value in kilometer is: %.2f\n", m_to_km(m));
      fprintf(fp, "%.2f m  = %.2f km\n", m, m_to_km(m));
    } else if (opt == 4) {
      float m;
      printf("Enter the value in meter: ");
      scanf("%f", &m);
      printf("The value in wa is: %.2f\n", m_to_wa(m));
      fprintf(fp, "%.2f m  = %.2f wa\n", m, m_to_wa(m));
    } else if (opt == 5) {
      float km;
      printf("Enter the value in kilometer: ");
      scanf("%f", &km);
      printf("The value in mile is: %.2f\n", km_to_mile(km));
      fprintf(fp, "%.2f km = %.2f mile\n", km, km_to_mile(km));
    }
    printf("\n");
  }

  fclose(fp);
  return 0;
}
