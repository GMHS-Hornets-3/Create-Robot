#include <kipr/botball.h>

void driveForward (int distance);
void driveBackwards (int distance);
void turnRight (int angle);
void turnLeft (int angle);
void stopAtLine (int value);
void stopAtLine2 (int value);
void senseBurning (int channel);
int main()
{
   
    create_connect();
    driveForward(500);
    turnLeft(105);
    stopAtLine(2150);
    turnLeft(105);
    stopAtLine(2150);
    senseBurning(0);
    create_stop();
    create_disconnect();
    return 0;
}

void driveForward (int distance)
{
    set_create_distance(0);
    while (abs(get_create_distance())<distance)
    {
        create_drive_direct(250,250);
    	msleep(10);
	}
}

void driveBackwards (int distance)
{
    set_create_distance(0);
    while (abs(get_create_distance())<distance)
    {
        create_drive_direct(-100,-100);
    	msleep(10);
	}
}

void turnRight (int angle)
{
    set_create_total_angle(0);
    while (abs(get_create_total_angle())<angle)
    {
        create_drive_direct(150,-150);
    	msleep(10);
	}
}
        
void turnLeft (int angle)
{
    set_create_total_angle(0);
    while (abs(get_create_total_angle())<angle)
    {
        create_drive_direct(-150,150);
        msleep(10);
    }
    
}
void stopAtLine (int value)
{
    while (get_create_lcliff_amt()&&get_create_rcliff_amt()>value)
    {
        create_drive_direct(250,250);
    	msleep(10);
    }
}
 
void stopAtLine2 (int value)
{
    while (get_create_lfcliff_amt()&&get_create_rfcliff_amt()>value)
    {
        create_drive_direct(250,250);
    	msleep(10);
    }
}

void senseBurning (int channel)
{
    camera_open_black();
    camera_update();
    if (get_object_count(channel)==1)
    {
        set_create_distance(0);
        while (abs(get_create_distance())<39)
    	{
        	create_drive_direct(-100,-100);
    		msleep(10);
		}
        set_create_total_angle(0);
    	while (abs(get_create_total_angle())<105)
    	{
        	create_drive_direct(-150,150);
    		msleep(10);
		}
    	set_create_distance(0);
    	while (abs(get_create_distance())<192)
    	{
        	create_drive_direct(250,250);
    		msleep(10);
		}
    	set_create_total_angle(0);
    	while (abs(get_create_total_angle())<105)
    	{
        	create_drive_direct(-150,150);
        	msleep(10);
    	}
        set_create_total_angle(0);
    	while (abs(get_create_total_angle())<210)
    	{
        	create_drive_direct(-150,150);
        	msleep(10);
    	}
    }
    else
        set_create_distance(0);
    	while (abs(get_create_distance())<115)
    	{
        	create_drive_direct(-100,-100);
    		msleep(10);
		}
    	set_create_total_angle(0);
    	while (abs(get_create_total_angle())<105)
    	{
        	create_drive_direct(150,-150);
    		msleep(10);
		}
        set_create_distance(0);
    	while (abs(get_create_distance())<192)
    	{
        	create_drive_direct(250,250);
    		msleep(10);
		}
     	set_create_total_angle(0);
    	while (abs(get_create_total_angle())<105)
    	{
        	create_drive_direct(150,-150);
    		msleep(10);
		}
	}
