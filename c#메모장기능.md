using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace 메모장
{
       public static class pub
    {
        public static string shredA = "";
    }
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void 새로만들기ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            textBox1.Text = "";
        }
        string filename = ""; //공용변수 만들어주기
        private void 열기ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            //1.사용에게 열 파일을 선택
            this.saveFileDialog1.Filter = "텍스트 문서(*.txt)|*txt.|모든파일|*.*";
            openFileDialog1.ShowDialog();
            //1-1 선택 파일 변수에 저장
            filename = openFileDialog1.FileName;
            //2.파일의 내용을 읽기
            string Data = System.IO.File.ReadAllText(filename); //오른쪽 데이터를 왼쪽 변수에 기록
            //3.화면에 표시
            textBox1.Text =Data;
        }

        private void 저장ToolStripMenuItem_Click(object sender, EventArgs e)
        {
            //그렇지 않으면 다른이름으로 저장과 동일
            if (filename == "")
            {
                // 1.사용자에게 저장할 파일 선택
                this.saveFileDialog1.ShowDialog();
                this.saveFileDialog1.Filter = "텍스트 문서(*.txt)|*txt.|모든파일|*.*";
                //2.파일 저장
                System.IO.File.WriteAllText(saveFileDialog1.FileName, textBox1.Text);
                //3.파일명 기억
                filename = saveFileDialog1.FileName;
            }
            else
            {
                //해당 파일명으로 현재 내용저장
                //2.파일저장.
                System.IO.File.WriteAllText(filename, textBox1.Text);
            }
        }

        private void 다른이름으로저장AToolStripMenuItem_Click(object sender, EventArgs e)
        {
            //1.사용자에게 저장파일 선택
            this.saveFileDialog1.Filter = "텍스트 문서(*.txt)|*txt.|모든파일|*.*";
            this.saveFileDialog1.ShowDialog();

            //2.파일 저장
            System.IO.File.WriteAllText(saveFileDialog1.FileName, textBox1.Text);
        }   //io는 입출력담당

        private void 끝내기XToolStripMenuItem_Click(object sender, EventArgs e)
        {
            //프로그램 종료
           this.Close();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            progressBar1.PerformStep(); //진행줄표시 앞으로 이동
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            progressBar1.Minimum = 0;
            progressBar1.Maximum = 100; 
            progressBar1.Value = 0;
            progressBar1.Step = 10;
        }
      
        Form2 f;
        private void button2_Click(object sender, EventArgs e)
        {
            f = new Form2("제목", this);
            f.Show();
        }

        private void button3_Click(object sender, EventArgs e)
        {
            MessageBox.Show(pub.shredA.ToString());

        }
    }
}
