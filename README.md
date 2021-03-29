using System;

using System.Collections.Generic;

using System.ComponentModel;

using System.Data;

using System.Drawing;

using System.Linq;

using System.Text;

using System.Threading.Tasks;

using System.Windows.Forms;

namespace QuickSort
{
    public partial class frmQuickSort : Form
    {
        List<int> nuevalista = new List<int>();
    
        public frmQuickSort()
        {
            InitializeComponent();
        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {

        }

        private void btnReiniciar_Click(object sender, EventArgs e)
        {
            lstOriginal.Items.Clear();
            lstOrdenada.Items.Clear();
        }

        private void btnAgregar_Click(object sender, EventArgs e)
        {
            int vector;
            
            vector = int.Parse(txtNro.Text);
            lstOriginal.Items.Add(vector);
            txtNro.Clear();
            txtNro.Focus();
            nuevalista.Add(vector);
        }

        private void btnOrdenar_Click(object sender, EventArgs e)
        {
            int[] nuli = nuevalista.ToArray();
            quicksort(nuli, 0, nuli.Length-1);
            
           
            foreach (var item in nuli)
            {
                lstOrdenada.Items.Add(item.ToString());
            }
        }

        private void quicksort(int[] vector, int primero, int ultimo)
        {
            int i, j, central;
            double pivote;
            central = (primero + ultimo) / 2;
            pivote = vector[central];
            i = primero;
            j = ultimo;
            do
            {
                while (vector[i] < pivote) i++;
                while (vector[j] > pivote) j--;
                if (i <= j)
                {
                    int temp;
                    temp = vector[i];
                    vector[i] = vector[j];
                    vector[j] = temp;
                    i++;
                    j--;
                }
            } while (i <= j);

            if (primero < j)
            {
                quicksort(vector, primero, j);
            }
            if (i < ultimo)
            {
                quicksort(vector, i, ultimo);
            }
        }
    }
}
