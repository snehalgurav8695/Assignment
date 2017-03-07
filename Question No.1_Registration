using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;
using Oracle.DataAccess.Client;

public partial class Registration : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
       if(!IsPostBack)
       {
           select();
       }
    }
    protected void select()
    {
         try
        {
            using(OracleConnection conn = new OracleConnection())
            using(OracleCommand cmd = new OracleCommand("select * from Registration", conn))
            {
                conn.Open();
                OracleDataReader reader = cmd.ExecuteReader();

                GridView1.DataSource = reader.Read(); ;

            }
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }
    
    protected void resetbtn_Click(object sender, EventArgs e)
    {
        usernmtxt.Text = "";
        passwordtxt.Text = " ";
        confrmpasstxt.Text = "";
        fnamtxt.Text = "";
        lnametxt.Text = "";
        emailtxt.Text = "";
        phnmtxt.Text = "";
        locationtxt.Text = "";

    }

    protected void GridView1_RowDeleting(object sender, GridViewDeleteEventArgs e)
    {
        try { 
        GridView1.DeleteRow(e.RowIndex);
        
        }catch(Exception ee)
        {
            Console.WriteLine(ee);
        }


        
    }
    protected void GridView1_RowEditing(object sender, GridViewEditEventArgs e)
    {
       
    }
    protected void GridView1_PageIndexChanging(object sender, GridViewPageEventArgs e)
    {

    }
    protected void savebtn_Click(object sender, EventArgs e)
    {
        string oradb = "Data Source=xe;User Id=system;Password=samyak;";
         OracleConnection conn = new OracleConnection(oradb);
try{
       
        conn.Open();
        OracleCommand cmd = new OracleCommand();
        cmd.Connection = conn;
        cmd.CommandText = "Insert into Registration values('" + usernmtxt.Text + "','" + passwordtxt.Text + "','" + fnamtxt.Text + "','" + lnametxt.Text + "','" + emailtxt.Text + "','" + phnmtxt.Text + "','" + locationtxt.Text + "')";
         cmd.ExecuteNonQuery();
}
        catch(Exception ee)
{
            Console.WriteLine(ee);
        }
        conn.Dispose();

        Response.Redirect("Registration.aspx");
    }
}
