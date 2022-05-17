using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace checkbox
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void UpdateLabel(String s, bool b)
        {
            if (b) 
                label1.Text += s;
            else
            {
                string strTemp = label1.Text;
                int i = strTemp.IndexOf(s); //문자열 가져온다
                label1.Text = strTemp.Remove(i,s.Length); //삭제후 내가 원하는 문자열 가져ㅇ온다


            }
        }
        private void checkBox1_CheckedChanged(object sender, EventArgs e)
        {
            UpdateLabel(checkBox1.Text, checkBox1.Checked);

        }

        private void checkBox2_CheckedChanged(object sender, EventArgs e)
        {
            UpdateLabel(checkBox2.Text, checkBox2.Checked);

        }

        private void checkBox3_CheckedChanged(object sender, EventArgs e)
        {
            UpdateLabel(checkBox2.Text, checkBox3.Checked);

        }

        private void checkBox4_CheckedChanged(object sender, EventArgs e)
        {
            UpdateLabel(checkBox2.Text, checkBox4.Checked);

        }
    }
}
