{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "name": "T flama adiabática.ipynb",
      "provenance": [],
      "authorship_tag": "ABX9TyO+AWWqyJpD5l8Ig638/Udj",
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/JManuelRG/cursopython/blob/main/2%20Uso%20de%20librer%C3%ADas/T%20flama%20adiab%C3%A1tica.ipynb\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "nrCOMhtsQnZL"
      },
      "source": [
        "![image.png](data:image/png;base64,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)"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "qFAWp1aEQp3O"
      },
      "source": [
        "dA = 43.471\n",
        "dB = 0.00950219\n",
        "dC = 0\n",
        "dD = -64460\n",
        "dHr = -802625 # J/mol\n",
        "R = 8.314 #J/mol"
      ],
      "execution_count": 26,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "NEOz4RocQntU"
      },
      "source": [
        "import sympy\n",
        "T = sympy.symbols('T')"
      ],
      "execution_count": 27,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 52
        },
        "id": "0PJDJNQFRS53",
        "outputId": "e119e83b-35dd-4dfe-99f0-97d2fb1edf17"
      },
      "source": [
        "integral = sympy.integrate(dA+dB*T+dC*T**2+dD*T**-2, (T,298.15,T))\n",
        "display(integral)"
      ],
      "execution_count": 35,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/latex": "$\\displaystyle 0.004751095 T^{2} + 43.471 T - 13599.4196445521 + \\frac{64460.0}{T}$",
            "text/plain": [
              "0.004751095*T**2 + 43.471*T - 13599.4196445521 + 64460.0/T"
            ]
          },
          "metadata": {
            "tags": []
          }
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 52
        },
        "id": "9MPEKkuFQ8_Y",
        "outputId": "88ad3b92-93f3-462d-84cb-4dfebc1a4ac1"
      },
      "source": [
        "ecuacion = sympy.Eq(dHr, -R*integral)\n",
        "display(ecuacion)"
      ],
      "execution_count": 36,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/latex": "$\\displaystyle -802625 = - 0.03950060383 T^{2} - 361.417894 T + 113065.574924807 - \\frac{535920.44}{T}$",
            "text/plain": [
              "Eq(-802625, -0.03950060383*T**2 - 361.417894*T + 113065.574924807 - 535920.44/T)"
            ]
          },
          "metadata": {
            "tags": []
          }
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "ddUv39kgRtW0",
        "outputId": "75538396-e052-4537-9e07-bc617dcf7d51"
      },
      "source": [
        "# Resolver para T\n",
        "Tflama= sympy.solve(ecuacion,T)\n",
        "print(Tflama)"
      ],
      "execution_count": 42,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "[-11216.530952605 + 0.e-19*I, 0.585398952004078 + 0.e-22*I, 2066.26532204321 + 0.e-19*I]\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "jtGRZXR6Uuql",
        "outputId": "6c94a79e-d560-497c-c162-600e21749dba"
      },
      "source": [
        "print(\"La temperatura de flama adiabática es:\")\n",
        "import math\n",
        "print((Tflama[2]))"
      ],
      "execution_count": 49,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "La temperatura de flama adiabática es:\n",
            "2066.26532204321 + 0.e-19*I\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "RBCY9LAuSkDt"
      },
      "source": [
        "# Resultado =\n",
        "$$T = 2066 K = 1793°C$$"
      ]
    }
  ]
}
