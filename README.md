# mesh.p
mesh analysisin calculation in c programing code..📌 
#include <stdio.h>

int main()
{
    float R1, R2, R3, V1, V2;
    float a, b, c, d, e, f;
    float D, D1, D2;
    float I1, I2;

    printf("Enter R1, R2 and common resistance R3 (ohms): ");
    scanf("%f %f %f", &R1, &R2, &R3);

    printf("Enter voltage sources V1 and V2 (volts): ");
    scanf("%f %f", &V1, &V2);

    // Mesh equations:
    // (R1+R3)I1 - R3I2 = V1
    // -R3I1 + (R2+R3)I2 = V2

    a = R1 + R3;
    b = -R3;
    c = -R3;
    d = R2 + R3;

    e = V1;
    f = V2;

    // Determinant
    D = a * d - b * c;

    if (D == 0)
    {
        printf("No unique solution exists.\n");
        return 0;
    }

    // Cramer's Rule
    D1 = e * d - b * f;
    D2 = a * f - e * c;

    I1 = D1 / D;
    I2 = D2 / D;

    printf("\n--- Mesh Analysis Result ---\n");
    printf("Mesh Current I1 = %.2f A\n", I1);
    printf("Mesh Current I2 = %.2f A\n", I2);

    return 0;
}
